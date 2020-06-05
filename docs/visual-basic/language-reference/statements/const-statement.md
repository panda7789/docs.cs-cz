---
title: Const – příkaz
ms.date: 05/12/2018
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
ms.openlocfilehash: 3b05d4067ef99e03df07d2c316c982051180d961
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84382104"
---
# <a name="const-statement-visual-basic"></a><span data-ttu-id="961e0-102">Const – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="961e0-102">Const Statement (Visual Basic)</span></span>

<span data-ttu-id="961e0-103">Deklaruje a definuje jednu nebo více konstant.</span><span class="sxs-lookup"><span data-stu-id="961e0-103">Declares and defines one or more constants.</span></span>

## <a name="syntax"></a><span data-ttu-id="961e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="961e0-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ]
Const constantlist
```

## <a name="parts"></a><span data-ttu-id="961e0-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="961e0-105">Parts</span></span>

`attributelist`  
<span data-ttu-id="961e0-106">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="961e0-106">Optional.</span></span> <span data-ttu-id="961e0-107">Seznam atributů, které se vztahují na všechny konstanty deklarované v tomto příkazu.</span><span class="sxs-lookup"><span data-stu-id="961e0-107">List of attributes that apply to all the constants declared in this statement.</span></span> <span data-ttu-id="961e0-108">Viz [seznam atributů](attribute-list.md) v lomených závorkách (" `<` " a " `>` ").</span><span class="sxs-lookup"><span data-stu-id="961e0-108">See [Attribute List](attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

`accessmodifier`  
<span data-ttu-id="961e0-109">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="961e0-109">Optional.</span></span> <span data-ttu-id="961e0-110">Toto použijte k určení, ke kterému kódu má přístup k těmto konstantám.</span><span class="sxs-lookup"><span data-stu-id="961e0-110">Use this to specify what code can access these constants.</span></span> <span data-ttu-id="961e0-111">Může být [Veřejná](../modifiers/public.md), [chráněná](../modifiers/protected.md), [Friend](../modifiers/friend.md), [Protected Friend](../modifiers/protected-friend.md), [Private](../modifiers/private.md)nebo [Private Protected](../modifiers/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="961e0-111">Can be [Public](../modifiers/public.md), [Protected](../modifiers/protected.md), [Friend](../modifiers/friend.md), [Protected Friend](../modifiers/protected-friend.md), [Private](../modifiers/private.md), or [Private Protected](../modifiers/private-protected.md).</span></span>

`Shadows`  
<span data-ttu-id="961e0-112">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="961e0-112">Optional.</span></span> <span data-ttu-id="961e0-113">Použijte k předeklaraci a skrytí programovacího prvku v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="961e0-113">Use this to redeclare and hide a programming element in a base class.</span></span> <span data-ttu-id="961e0-114">Viz [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="961e0-114">See [Shadows](../modifiers/shadows.md).</span></span>

`constantlist`  
<span data-ttu-id="961e0-115">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="961e0-115">Required.</span></span> <span data-ttu-id="961e0-116">Seznam konstant, které jsou deklarovány v tomto příkazu.</span><span class="sxs-lookup"><span data-stu-id="961e0-116">List of constants being declared in this statement.</span></span>

<span data-ttu-id="961e0-117">`constant` `[ ,` `constant` `... ]`</span><span class="sxs-lookup"><span data-stu-id="961e0-117">`constant` `[ ,` `constant` `... ]`</span></span>

<span data-ttu-id="961e0-118">Každá `constant` z nich má následující syntaxi a části:</span><span class="sxs-lookup"><span data-stu-id="961e0-118">Each `constant` has the following syntax and parts:</span></span>

<span data-ttu-id="961e0-119">`constantname` `[ As` `datatype` `] =` `initializer`</span><span class="sxs-lookup"><span data-stu-id="961e0-119">`constantname` `[ As` `datatype` `] =` `initializer`</span></span>

|<span data-ttu-id="961e0-120">Část</span><span class="sxs-lookup"><span data-stu-id="961e0-120">Part</span></span>|<span data-ttu-id="961e0-121">Description</span><span class="sxs-lookup"><span data-stu-id="961e0-121">Description</span></span>|
|----------|-----------------|
|`constantname`|<span data-ttu-id="961e0-122">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="961e0-122">Required.</span></span> <span data-ttu-id="961e0-123">Název konstanty.</span><span class="sxs-lookup"><span data-stu-id="961e0-123">Name of the constant.</span></span> <span data-ttu-id="961e0-124">Viz [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="961e0-124">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`datatype`|<span data-ttu-id="961e0-125">Požadováno v `Option Strict` případě `On` , že je.</span><span class="sxs-lookup"><span data-stu-id="961e0-125">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="961e0-126">Datový typ konstanty.</span><span class="sxs-lookup"><span data-stu-id="961e0-126">Data type of the constant.</span></span>|
|`initializer`|<span data-ttu-id="961e0-127">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="961e0-127">Required.</span></span> <span data-ttu-id="961e0-128">Výraz vyhodnocený v době kompilace a přiřazený konstantě</span><span class="sxs-lookup"><span data-stu-id="961e0-128">Expression that is evaluated at compile time and assigned to the constant.</span></span>|

## <a name="remarks"></a><span data-ttu-id="961e0-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="961e0-129">Remarks</span></span>

<span data-ttu-id="961e0-130">Pokud máte hodnotu, která se ve vaší aplikaci nikdy nemění, můžete definovat pojmenovanou konstantu a použít ji místo hodnoty literálu.</span><span class="sxs-lookup"><span data-stu-id="961e0-130">If you have a value that never changes in your application, you can define a named constant and use it in place of a literal value.</span></span> <span data-ttu-id="961e0-131">Název je snazší pamatovat než hodnota.</span><span class="sxs-lookup"><span data-stu-id="961e0-131">A name is easier to remember than a value.</span></span> <span data-ttu-id="961e0-132">Konstantu můžete definovat pouze jednou a použít ji na mnoha místech kódu.</span><span class="sxs-lookup"><span data-stu-id="961e0-132">You can define the constant just once and use it in many places in your code.</span></span> <span data-ttu-id="961e0-133">Pokud v novější verzi potřebujete znovu definovat hodnotu, `Const` je příkaz jediným místem, které potřebujete k provedení změny.</span><span class="sxs-lookup"><span data-stu-id="961e0-133">If in a later version you need to redefine the value, the `Const` statement is the only place you need to make a change.</span></span>

<span data-ttu-id="961e0-134">Můžete použít `Const` pouze v modulu nebo v úrovni procedury.</span><span class="sxs-lookup"><span data-stu-id="961e0-134">You can use `Const` only at module or procedure level.</span></span> <span data-ttu-id="961e0-135">To znamená, že *kontext deklarace* proměnné musí být třída, struktura, modul, procedura nebo blok a nemůže se jednat o zdrojový soubor, obor názvů nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="961e0-135">This means the *declaration context* for a variable must be a class, structure, module, procedure, or block, and cannot be a source file, namespace, or interface.</span></span> <span data-ttu-id="961e0-136">Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="961e0-136">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="961e0-137">Místní konstanty (uvnitř procedury) jako výchozí pro veřejný přístup a nemůžete použít žádné modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="961e0-137">Local constants (inside a procedure) default to public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="961e0-138">Konstanty členů třídy a modulu (mimo jakákoli procedura) výchozí pro privátní přístup a členské konstanty struktury jsou standardně přístupné pro veřejný přístup.</span><span class="sxs-lookup"><span data-stu-id="961e0-138">Class and module member constants (outside any procedure) default to private access, and structure member constants default to public access.</span></span> <span data-ttu-id="961e0-139">Můžete upravit jejich úrovně přístupu modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="961e0-139">You can adjust their access levels with the access modifiers.</span></span>

## <a name="rules"></a><span data-ttu-id="961e0-140">Pravidla</span><span class="sxs-lookup"><span data-stu-id="961e0-140">Rules</span></span>

- <span data-ttu-id="961e0-141">**Kontext deklarace**</span><span class="sxs-lookup"><span data-stu-id="961e0-141">**Declaration Context.**</span></span> <span data-ttu-id="961e0-142">Konstanta deklarovaná na úrovni modulu, mimo jakoukoli proceduru, je *členská konstanta*; je členem třídy, struktury nebo modulu, který je deklaruje.</span><span class="sxs-lookup"><span data-stu-id="961e0-142">A constant declared at module level, outside any procedure, is a *member constant*; it is a member of the class, structure, or module that declares it.</span></span>

  <span data-ttu-id="961e0-143">Konstanta deklarovaná na úrovni procedury je *místní konstanta*; je místní pro proceduru nebo blok, který je deklaruje.</span><span class="sxs-lookup"><span data-stu-id="961e0-143">A constant declared at procedure level is a *local constant*; it is local to the procedure or block that declares it.</span></span>

- <span data-ttu-id="961e0-144">**Atribut.**</span><span class="sxs-lookup"><span data-stu-id="961e0-144">**Attributes.**</span></span> <span data-ttu-id="961e0-145">Atributy lze použít pouze pro členské konstanty, nikoli pro místní konstanty.</span><span class="sxs-lookup"><span data-stu-id="961e0-145">You can apply attributes only to member constants, not to local constants.</span></span> <span data-ttu-id="961e0-146">Atribut přispívá k metadatům sestavení, která nejsou smysluplná pro dočasné úložiště, jako jsou například místní konstanty.</span><span class="sxs-lookup"><span data-stu-id="961e0-146">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local constants.</span></span>

- <span data-ttu-id="961e0-147">**Modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="961e0-147">**Modifiers.**</span></span> <span data-ttu-id="961e0-148">Ve výchozím nastavení jsou všechny konstanty `Shared` , `Static` a `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="961e0-148">By default, all constants are `Shared`, `Static`, and `ReadOnly`.</span></span> <span data-ttu-id="961e0-149">Při deklaraci konstanty nemůžete použít žádná z těchto klíčových slov.</span><span class="sxs-lookup"><span data-stu-id="961e0-149">You cannot use any of these keywords when declaring a constant.</span></span>

  <span data-ttu-id="961e0-150">Na úrovni procedury nemůžete použít `Shadows` ani žádné modifikátory přístupu k deklaraci místních konstant.</span><span class="sxs-lookup"><span data-stu-id="961e0-150">At procedure level, you cannot use `Shadows` or any access modifiers to declare local constants.</span></span>

- <span data-ttu-id="961e0-151">**Několik konstant.**</span><span class="sxs-lookup"><span data-stu-id="961e0-151">**Multiple Constants.**</span></span> <span data-ttu-id="961e0-152">Můžete deklarovat několik konstant v rámci jednoho příkazu deklarace a určit tak `constantname` část pro každé z nich.</span><span class="sxs-lookup"><span data-stu-id="961e0-152">You can declare several constants in the same declaration statement, specifying the `constantname` part for each one.</span></span> <span data-ttu-id="961e0-153">Vícenásobné konstanty jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="961e0-153">Multiple constants are separated by commas.</span></span>

## <a name="data-type-rules"></a><span data-ttu-id="961e0-154">Pravidla datového typu</span><span class="sxs-lookup"><span data-stu-id="961e0-154">Data Type Rules</span></span>

- <span data-ttu-id="961e0-155">**Datové typy.**</span><span class="sxs-lookup"><span data-stu-id="961e0-155">**Data Types.**</span></span> <span data-ttu-id="961e0-156">`Const`Příkaz může deklarovat datový typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="961e0-156">The `Const` statement can declare the data type of a variable.</span></span> <span data-ttu-id="961e0-157">Můžete zadat libovolný datový typ nebo název výčtu.</span><span class="sxs-lookup"><span data-stu-id="961e0-157">You can specify any data type or the name of an enumeration.</span></span>

- <span data-ttu-id="961e0-158">**Výchozí typ**</span><span class="sxs-lookup"><span data-stu-id="961e0-158">**Default Type.**</span></span> <span data-ttu-id="961e0-159">Pokud nezadáte `datatype` , konstanta převezme datový typ `initializer` .</span><span class="sxs-lookup"><span data-stu-id="961e0-159">If you do not specify `datatype`, the constant takes the data type of `initializer`.</span></span> <span data-ttu-id="961e0-160">Pokud zadáte obojí `datatype` a `initializer` , datový typ `initializer` musí být převoditelné na `datatype` .</span><span class="sxs-lookup"><span data-stu-id="961e0-160">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="961e0-161">V případě `datatype` `initializer` , že není k dispozici ani, je výchozím datovým typem `Object` .</span><span class="sxs-lookup"><span data-stu-id="961e0-161">If neither `datatype` nor `initializer` is present, the data type defaults to `Object`.</span></span>

- <span data-ttu-id="961e0-162">**Různé typy.**</span><span class="sxs-lookup"><span data-stu-id="961e0-162">**Different Types.**</span></span> <span data-ttu-id="961e0-163">Pro `As` každou proměnnou, kterou deklarujete, můžete zadat různé typy dat pro různé konstanty.</span><span class="sxs-lookup"><span data-stu-id="961e0-163">You can specify different data types for different constants by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="961e0-164">Nelze však deklarovat několik konstant, které mají být stejného typu pomocí `As` klauzule Common.</span><span class="sxs-lookup"><span data-stu-id="961e0-164">However, you cannot declare several constants to be of the same type by using a common `As` clause.</span></span>

- <span data-ttu-id="961e0-165">**Operace.**</span><span class="sxs-lookup"><span data-stu-id="961e0-165">**Initialization.**</span></span> <span data-ttu-id="961e0-166">Je nutné inicializovat hodnotu každé konstanty v `constantlist` .</span><span class="sxs-lookup"><span data-stu-id="961e0-166">You must initialize the value of every constant in `constantlist`.</span></span> <span data-ttu-id="961e0-167">Použijete `initializer` k poskytnutí výrazu, který se má přiřadit konstantě.</span><span class="sxs-lookup"><span data-stu-id="961e0-167">You use `initializer` to supply an expression to be assigned to the constant.</span></span> <span data-ttu-id="961e0-168">Výraz může být libovolná kombinace literálů, dalších konstant, které jsou již definovány, a členů výčtu, které jsou již definovány.</span><span class="sxs-lookup"><span data-stu-id="961e0-168">The expression can be any combination of literals, other constants that are already defined, and enumeration members that are already defined.</span></span> <span data-ttu-id="961e0-169">K kombinování takových prvků lze použít aritmetické a logické operátory.</span><span class="sxs-lookup"><span data-stu-id="961e0-169">You can use arithmetic and logical operators to combine such elements.</span></span>

  <span data-ttu-id="961e0-170">V nástroji nelze použít proměnné nebo funkce `initializer` .</span><span class="sxs-lookup"><span data-stu-id="961e0-170">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="961e0-171">Můžete však použít klíčová slova převodu, jako je `CByte` a `CShort` .</span><span class="sxs-lookup"><span data-stu-id="961e0-171">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="961e0-172">Můžete také použít, `AscW` Pokud je volána s konstantou `String` nebo `Char` argumentem, protože lze vyhodnotit v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="961e0-172">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>

## <a name="behavior"></a><span data-ttu-id="961e0-173">Chování</span><span class="sxs-lookup"><span data-stu-id="961e0-173">Behavior</span></span>

- <span data-ttu-id="961e0-174">**Oboru.**</span><span class="sxs-lookup"><span data-stu-id="961e0-174">**Scope.**</span></span> <span data-ttu-id="961e0-175">Místní konstanty jsou přístupné pouze v rámci jejich procedury nebo bloku.</span><span class="sxs-lookup"><span data-stu-id="961e0-175">Local constants are accessible only from within their procedure or block.</span></span> <span data-ttu-id="961e0-176">Konstanty členů jsou přístupné odkudkoli v rámci své třídy, struktury nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="961e0-176">Member constants are accessible from anywhere within their class, structure, or module.</span></span>

- <span data-ttu-id="961e0-177">**Vydal.**</span><span class="sxs-lookup"><span data-stu-id="961e0-177">**Qualification.**</span></span> <span data-ttu-id="961e0-178">Kód mimo třídu, strukturu nebo modul musí kvalifikovat název členské konstanty s názvem této třídy, struktury nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="961e0-178">Code outside a class, structure, or module must qualify a member constant's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="961e0-179">Kód mimo proceduru nebo blok nemůže odkazovat na žádné místní konstanty v rámci tohoto postupu nebo bloku.</span><span class="sxs-lookup"><span data-stu-id="961e0-179">Code outside a procedure or block cannot refer to any local constants within that procedure or block.</span></span>

## <a name="example"></a><span data-ttu-id="961e0-180">Příklad</span><span class="sxs-lookup"><span data-stu-id="961e0-180">Example</span></span>

<span data-ttu-id="961e0-181">Následující příklad používá `Const` příkaz k deklaraci konstant pro použití namísto hodnot literálů.</span><span class="sxs-lookup"><span data-stu-id="961e0-181">The following example uses the `Const` statement to declare constants for use in place of literal values.</span></span>

[!code-vb[VbVbalrStatements#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#13)]

## <a name="example"></a><span data-ttu-id="961e0-182">Příklad</span><span class="sxs-lookup"><span data-stu-id="961e0-182">Example</span></span>

<span data-ttu-id="961e0-183">Definujete-li konstantu s datovým typem `Object` , kompilátor Visual Basic poskytne typu `initializer` místo `Object` .</span><span class="sxs-lookup"><span data-stu-id="961e0-183">If you define a constant with data type `Object`, the Visual Basic compiler gives it the type of `initializer`, instead of `Object`.</span></span> <span data-ttu-id="961e0-184">V následujícím příkladu má konstanta běhový `naturalLogBase` typ `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="961e0-184">In the following example, the constant `naturalLogBase` has the run-time type `Decimal`.</span></span>

[!code-vb[VbVbalrStatements#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#87)]

<span data-ttu-id="961e0-185">Předchozí příklad používá <xref:System.Type.ToString%2A> metodu u <xref:System.Type> objektu vráceného [operátorem GetType](../operators/gettype-operator.md), protože <xref:System.Type> nelze převést na `String` použití `CStr` .</span><span class="sxs-lookup"><span data-stu-id="961e0-185">The preceding example uses the <xref:System.Type.ToString%2A> method on the <xref:System.Type> object returned by the [GetType Operator](../operators/gettype-operator.md), because <xref:System.Type> cannot be converted to `String` using `CStr`.</span></span>

## <a name="see-also"></a><span data-ttu-id="961e0-186">Viz také</span><span class="sxs-lookup"><span data-stu-id="961e0-186">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [<span data-ttu-id="961e0-187">Enum – příkaz</span><span class="sxs-lookup"><span data-stu-id="961e0-187">Enum Statement</span></span>](enum-statement.md)
- [<span data-ttu-id="961e0-188">#Const direktiva</span><span class="sxs-lookup"><span data-stu-id="961e0-188">#Const Directive</span></span>](../directives/const-directive.md)
- [<span data-ttu-id="961e0-189">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="961e0-189">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="961e0-190">ReDim – příkaz</span><span class="sxs-lookup"><span data-stu-id="961e0-190">ReDim Statement</span></span>](redim-statement.md)
- [<span data-ttu-id="961e0-191">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="961e0-191">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="961e0-192">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="961e0-192">Constants and Enumerations</span></span>](../../programming-guide/language-features/constants-enums/index.md)
- [<span data-ttu-id="961e0-193">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="961e0-193">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
- [<span data-ttu-id="961e0-194">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="961e0-194">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
