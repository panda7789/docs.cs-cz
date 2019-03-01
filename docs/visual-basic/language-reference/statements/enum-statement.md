---
title: Enum – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: 662dc63b69a8229693471909a50b0c4f336b5637
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965693"
---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="45512-102">Enum – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45512-102">Enum Statement (Visual Basic)</span></span>
<span data-ttu-id="45512-103">Deklaruje výčet a definuje hodnoty jeho členů.</span><span class="sxs-lookup"><span data-stu-id="45512-103">Declares an enumeration and defines the values of its members.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45512-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45512-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a><span data-ttu-id="45512-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="45512-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="45512-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="45512-106">Optional.</span></span> <span data-ttu-id="45512-107">Seznam atributů, které platí pro tento výčet.</span><span class="sxs-lookup"><span data-stu-id="45512-107">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="45512-108">Je nutné uzavřít [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) v lomených závorkách ("`<`"a"`>`").</span><span class="sxs-lookup"><span data-stu-id="45512-108">You must enclose the [attribute list](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
     <span data-ttu-id="45512-109"><xref:System.FlagsAttribute> Atribut označuje, že hodnota instance výčtu může obsahovat více členů výčtu a, že každý člen představuje bitového pole hodnoty výčtu.</span><span class="sxs-lookup"><span data-stu-id="45512-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="45512-110">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="45512-110">Optional.</span></span> <span data-ttu-id="45512-111">Určuje, jaký kód může přistupovat k tento výčet.</span><span class="sxs-lookup"><span data-stu-id="45512-111">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="45512-112">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="45512-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="45512-113">Public</span><span class="sxs-lookup"><span data-stu-id="45512-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="45512-114">Protected</span><span class="sxs-lookup"><span data-stu-id="45512-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="45512-115">Friend</span><span class="sxs-lookup"><span data-stu-id="45512-115">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="45512-116">Private</span><span class="sxs-lookup"><span data-stu-id="45512-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [<span data-ttu-id="45512-117">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="45512-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)
    
    - [<span data-ttu-id="45512-118">Private Protected</span><span class="sxs-lookup"><span data-stu-id="45512-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

-   `Shadows`  
  
     <span data-ttu-id="45512-119">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="45512-119">Optional.</span></span> <span data-ttu-id="45512-120">Určuje, že tento výčet znovu deklaruje a skryje identicky pojmenovanou programovací prvek, nebo sadu přetížených elementů v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="45512-120">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="45512-121">Můžete zadat [stíny](../../../visual-basic/language-reference/modifiers/shadows.md) pouze na samotného výčtu, nikoli na kterýkoli z jejích členů.</span><span class="sxs-lookup"><span data-stu-id="45512-121">You can specify [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>  
  
-   `enumerationname`  
  
     <span data-ttu-id="45512-122">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="45512-122">Required.</span></span> <span data-ttu-id="45512-123">Název výčtu.</span><span class="sxs-lookup"><span data-stu-id="45512-123">Name of the enumeration.</span></span> <span data-ttu-id="45512-124">Informace o platné názvy najdete v tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="45512-124">For information on valid names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `datatype`  
  
     <span data-ttu-id="45512-125">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="45512-125">Optional.</span></span> <span data-ttu-id="45512-126">Datový typ výčtu a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="45512-126">Data type of the enumeration and all its members.</span></span>  
  
-   `memberlist`  
  
     <span data-ttu-id="45512-127">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="45512-127">Required.</span></span> <span data-ttu-id="45512-128">Seznam členů konstanty deklarované v tomto prohlášení.</span><span class="sxs-lookup"><span data-stu-id="45512-128">List of member constants being declared in this statement.</span></span> <span data-ttu-id="45512-129">Víc členů se zobrazí na jednotlivé zdrojové řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="45512-129">Multiple members appear on individual source code lines.</span></span>  
  
     <span data-ttu-id="45512-130">Každý `member` má následující syntaxi a části: `[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="45512-130">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="45512-131">Část</span><span class="sxs-lookup"><span data-stu-id="45512-131">Part</span></span>|<span data-ttu-id="45512-132">Popis</span><span class="sxs-lookup"><span data-stu-id="45512-132">Description</span></span>|  
    |---|---|  
    |`membername`|<span data-ttu-id="45512-133">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="45512-133">Required.</span></span> <span data-ttu-id="45512-134">Název tohoto člena.</span><span class="sxs-lookup"><span data-stu-id="45512-134">Name of this member.</span></span>|  
    |`initializer`|<span data-ttu-id="45512-135">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="45512-135">Optional.</span></span> <span data-ttu-id="45512-136">Výraz, který je vyhodnocen v době kompilace a přiřazené k tomuto členu.</span><span class="sxs-lookup"><span data-stu-id="45512-136">Expression that is evaluated at compile time and assigned to this member.</span></span>|  
  
-   <span data-ttu-id="45512-137">`End``Enum`</span><span class="sxs-lookup"><span data-stu-id="45512-137">`End` `Enum`</span></span>  
  
     <span data-ttu-id="45512-138">Ukončuje `Enum` bloku.</span><span class="sxs-lookup"><span data-stu-id="45512-138">Terminates the `Enum` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45512-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45512-139">Remarks</span></span>  
 <span data-ttu-id="45512-140">Pokud máte sadu neměnné hodnot, které logicky vzájemně souvisí, můžete je definovat společně ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="45512-140">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="45512-141">To umožňuje smysluplné názvy výčtu a její členy, které jsou jednodušší mějte na paměti než jejich hodnoty.</span><span class="sxs-lookup"><span data-stu-id="45512-141">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="45512-142">Pak můžete použít členy výčtu na mnoha místech ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="45512-142">You can then use the enumeration members in many places in your code.</span></span>  
  
 <span data-ttu-id="45512-143">Mezi výhody používání výčtů, patří:</span><span class="sxs-lookup"><span data-stu-id="45512-143">The benefits of using enumerations include the following:</span></span>  
  
-   <span data-ttu-id="45512-144">Snižuje chyby způsobené transpozice nebo chybným zadáním čísla.</span><span class="sxs-lookup"><span data-stu-id="45512-144">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="45512-145">Umožňuje snadno ke změně hodnot v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="45512-145">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="45512-146">Díky kód lépe čitelný, což znamená, že je méně pravděpodobné, že budou zavedeny chyby.</span><span class="sxs-lookup"><span data-stu-id="45512-146">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>  
  
-   <span data-ttu-id="45512-147">Zajišťuje kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="45512-147">Ensures forward compatibility.</span></span> <span data-ttu-id="45512-148">Pokud používáte výčty, váš kód je méně pravděpodobné, že selhat, pokud v budoucnu někdo změní hodnoty odpovídající názvy členů.</span><span class="sxs-lookup"><span data-stu-id="45512-148">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
 <span data-ttu-id="45512-149">Výčet má název, příslušný datový typ a sadu členů.</span><span class="sxs-lookup"><span data-stu-id="45512-149">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="45512-150">Každý člen představuje konstantu.</span><span class="sxs-lookup"><span data-stu-id="45512-150">Each member represents a constant.</span></span>  
  
 <span data-ttu-id="45512-151">Výčet deklarována třída, struktura, modul nebo rozhraní úroveň mimo všechny procedury, je *člen výčtu*.</span><span class="sxs-lookup"><span data-stu-id="45512-151">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="45512-152">Je členem třídy, struktury, modul nebo rozhraní, které se deklaruje.</span><span class="sxs-lookup"><span data-stu-id="45512-152">It is a member of the class, structure, module, or interface that declares it.</span></span>  
  
 <span data-ttu-id="45512-153">Výčty člen je přístupný z kdekoli v rámci třídy, struktury, modul nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="45512-153">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="45512-154">Kód mimo třídu, strukturu nebo modul musí kvalifikovat název člena výčtu s názvem této třídy, struktury nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="45512-154">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="45512-155">Vyhnete nutnosti použití plně kvalifikovaných názvů tak, že přidáte [importy](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) příkaz ke zdrojovému souboru.</span><span class="sxs-lookup"><span data-stu-id="45512-155">You can avoid the need to use fully qualified names by adding an [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>  
  
 <span data-ttu-id="45512-156">Výčet deklarován na úrovni oboru názvů, mimo třídu, strukturu, modul nebo rozhraní, je členem oboru názvů, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="45512-156">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>  
  
 <span data-ttu-id="45512-157">*Kontext deklarace* pro výčet musí být zdrojový soubor, obor názvů, třída, struktura, modul nebo rozhraní a nemůže být procedurou.</span><span class="sxs-lookup"><span data-stu-id="45512-157">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="45512-158">Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="45512-158">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="45512-159">Můžete použít atributy k vyčíslení jako celek, ale ne k jeho členy jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="45512-159">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="45512-160">Atribut přispívá informací o metadatech sestavení.</span><span class="sxs-lookup"><span data-stu-id="45512-160">An attribute contributes information to the assembly's metadata.</span></span>  
  
## <a name="data-type"></a><span data-ttu-id="45512-161">Datový typ</span><span class="sxs-lookup"><span data-stu-id="45512-161">Data Type</span></span>  
 <span data-ttu-id="45512-162">`Enum` Příkazu můžete deklarovat datový typ výčtu.</span><span class="sxs-lookup"><span data-stu-id="45512-162">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="45512-163">Každý člen má datový typ výčtu.</span><span class="sxs-lookup"><span data-stu-id="45512-163">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="45512-164">Můžete zadat `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, nebo `UShort`.</span><span class="sxs-lookup"><span data-stu-id="45512-164">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>  
  
 <span data-ttu-id="45512-165">Pokud nezadáte `datatype` pro výčet, každý člen má datový typ jeho `initializer`.</span><span class="sxs-lookup"><span data-stu-id="45512-165">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="45512-166">Pokud zadáte obě `datatype` a `initializer`, datový typ `initializer` musí být převeditelný na `datatype`.</span><span class="sxs-lookup"><span data-stu-id="45512-166">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="45512-167">Pokud ani `datatype` ani `initializer` je k dispozici, výchozí hodnota je typu dat `Integer`.</span><span class="sxs-lookup"><span data-stu-id="45512-167">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>  
  
## <a name="initializing-members"></a><span data-ttu-id="45512-168">Inicializace členů</span><span class="sxs-lookup"><span data-stu-id="45512-168">Initializing Members</span></span>  
 <span data-ttu-id="45512-169">`Enum` Příkazu můžete inicializovat obsah vybrané členy v `memberlist`.</span><span class="sxs-lookup"><span data-stu-id="45512-169">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="45512-170">Použijete `initializer` zadat výraz, který má být přiřazena k členu.</span><span class="sxs-lookup"><span data-stu-id="45512-170">You use `initializer` to supply an expression to be assigned to the member.</span></span>  
  
 <span data-ttu-id="45512-171">Pokud nezadáte `initializer` pro člena, Visual Basic inicializuje ji buď na hodnotu nula (Pokud je první `member` v `memberlist`), nebo na hodnotu větší než bezprostředně před jednou `member`.</span><span class="sxs-lookup"><span data-stu-id="45512-171">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>  
  
 <span data-ttu-id="45512-172">Výraz zadaný v každém `initializer` může být libovolná kombinace literály, jiné konstanty, které jsou již definovány a členy výčtu, které jsou již definovány, včetně předchozí členů tohoto výčtu.</span><span class="sxs-lookup"><span data-stu-id="45512-172">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="45512-173">Aritmetické a logické operátory můžete kombinovat takovýchto prvků.</span><span class="sxs-lookup"><span data-stu-id="45512-173">You can use arithmetic and logical operators to combine such elements.</span></span>  
  
 <span data-ttu-id="45512-174">Nelze použít proměnné nebo funkce v `initializer`.</span><span class="sxs-lookup"><span data-stu-id="45512-174">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="45512-175">Ale můžete použít klíčová slova převodu například `CByte` a `CShort`.</span><span class="sxs-lookup"><span data-stu-id="45512-175">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="45512-176">Můžete také použít `AscW` při volání s konstantou `String` nebo `Char` argument, protože, který může být vyhodnocen v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="45512-176">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>  
  
 <span data-ttu-id="45512-177">Výčty nemůžou mít hodnoty s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="45512-177">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="45512-178">Pokud člen je přiřazena hodnota s plovoucí desetinnou čárkou a `Option Strict` nastavená na on, dojde k chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="45512-178">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="45512-179">Pokud `Option Strict` je vypnuté, hodnota je automaticky převedena na `Enum` typu.</span><span class="sxs-lookup"><span data-stu-id="45512-179">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="45512-180">Pokud hodnotu členu překračuje povolený rozsah pro příslušný datový typ, nebo pokud je inicializovat kteréhokoli člena na maximální hodnotu povolenou příslušný datový typ, kompilátor nahlásí chybu.</span><span class="sxs-lookup"><span data-stu-id="45512-180">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>  
  
## <a name="modifiers"></a><span data-ttu-id="45512-181">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="45512-181">Modifiers</span></span>  
 <span data-ttu-id="45512-182">Třída, struktura, modul a rozhraní člen výčty výchozí veřejný přístup.</span><span class="sxs-lookup"><span data-stu-id="45512-182">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="45512-183">Můžete nastavit jejich úrovně přístupu modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="45512-183">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="45512-184">Namespace člen výčty výchozí přístup typu friend.</span><span class="sxs-lookup"><span data-stu-id="45512-184">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="45512-185">Můžete nastavit jejich úrovně veřejnosti, ale ne k soukromé nebo chráněné.</span><span class="sxs-lookup"><span data-stu-id="45512-185">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="45512-186">Další informace najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="45512-186">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="45512-187">Všechny členy výčtu mít veřejný přístup a žádné modifikátory přístupu nelze použít na ně.</span><span class="sxs-lookup"><span data-stu-id="45512-187">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="45512-188">Ale pokud stejný jako daný výčet má omezenější úroveň přístupu, úroveň přístupu zadaný výčet má přednost.</span><span class="sxs-lookup"><span data-stu-id="45512-188">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>  
  
 <span data-ttu-id="45512-189">Ve výchozím nastavení všechny výčty jsou typy a jejich polí jsou konstanty.</span><span class="sxs-lookup"><span data-stu-id="45512-189">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="45512-190">Proto `Shared`, `Static`, a `ReadOnly` klíčová slova nelze použít při deklaraci výčtu ani jejích členů.</span><span class="sxs-lookup"><span data-stu-id="45512-190">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>  
  
## <a name="assigning-multiple-values"></a><span data-ttu-id="45512-191">Přiřazení více hodnot</span><span class="sxs-lookup"><span data-stu-id="45512-191">Assigning Multiple Values</span></span>  
 <span data-ttu-id="45512-192">Výčty obvykle představují vzájemně se vylučuje hodnoty.</span><span class="sxs-lookup"><span data-stu-id="45512-192">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="45512-193">Zahrnutím <xref:System.FlagsAttribute> atribut `Enum` prohlášení, můžete místo toho přiřadit víc hodnot do instance výčtu.</span><span class="sxs-lookup"><span data-stu-id="45512-193">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="45512-194"><xref:System.FlagsAttribute> Atribut určuje, že výčet považovány za bitové pole, to znamená, že sada příznaků.</span><span class="sxs-lookup"><span data-stu-id="45512-194">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="45512-195">Toto nastavení se nazývá *bitový* výčty.</span><span class="sxs-lookup"><span data-stu-id="45512-195">These are called *bitwise* enumerations.</span></span>  
  
 <span data-ttu-id="45512-196">Pokud deklarujete výčet pomocí <xref:System.FlagsAttribute> atribut, doporučujeme použít mocninu 2, který je 1, 2, 4, 8, 16 a tak dále, pro hodnoty.</span><span class="sxs-lookup"><span data-stu-id="45512-196">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="45512-197">Doporučujeme také, že "None" být jméno člena, jehož hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="45512-197">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="45512-198">Další pokyny najdete v části <xref:System.FlagsAttribute> a <xref:System.Enum>.</span><span class="sxs-lookup"><span data-stu-id="45512-198">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45512-199">Příklad</span><span class="sxs-lookup"><span data-stu-id="45512-199">Example</span></span>  
 <span data-ttu-id="45512-200">Následující příklad ukazuje způsob použití `Enum` příkazu.</span><span class="sxs-lookup"><span data-stu-id="45512-200">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="45512-201">Všimněte si, že člen se označuje jako `EggSizeEnum.Medium`a ne jako `Medium`.</span><span class="sxs-lookup"><span data-stu-id="45512-201">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>  
  
 [!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="45512-202">Příklad</span><span class="sxs-lookup"><span data-stu-id="45512-202">Example</span></span>  
 <span data-ttu-id="45512-203">Metoda v následujícím příkladu je mimo `Egg` třídy.</span><span class="sxs-lookup"><span data-stu-id="45512-203">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="45512-204">Proto `EggSizeEnum` je plně kvalifikovaný jako `Egg.EggSizeEnum`.</span><span class="sxs-lookup"><span data-stu-id="45512-204">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>  
  
 [!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]  
  
## <a name="example"></a><span data-ttu-id="45512-205">Příklad</span><span class="sxs-lookup"><span data-stu-id="45512-205">Example</span></span>  
 <span data-ttu-id="45512-206">V následujícím příkladu `Enum` příkaz k definování související sadu s názvem konstantní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="45512-206">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="45512-207">V tomto případě hodnoty jsou barvy, které můžete se rozhodnout pro návrh formulářů pro zadávání dat pro databázi.</span><span class="sxs-lookup"><span data-stu-id="45512-207">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>  
  
 [!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="45512-208">Příklad</span><span class="sxs-lookup"><span data-stu-id="45512-208">Example</span></span>  
 <span data-ttu-id="45512-209">Následující příklad ukazuje hodnoty, které obsahují kladná a záporná čísla.</span><span class="sxs-lookup"><span data-stu-id="45512-209">The following example shows values that include both positive and negative numbers.</span></span>  
  
 [!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]  
  
## <a name="example"></a><span data-ttu-id="45512-210">Příklad</span><span class="sxs-lookup"><span data-stu-id="45512-210">Example</span></span>  
 <span data-ttu-id="45512-211">V následujícím příkladu `As` klauzule slouží k určení `datatype` výčtu.</span><span class="sxs-lookup"><span data-stu-id="45512-211">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>  
  
 [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="45512-212">Příklad</span><span class="sxs-lookup"><span data-stu-id="45512-212">Example</span></span>  
 <span data-ttu-id="45512-213">Následující příklad ukazuje, jak použít bitový výčtu.</span><span class="sxs-lookup"><span data-stu-id="45512-213">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="45512-214">Víc hodnot je přiřadit k instanci bitové operace výčtu.</span><span class="sxs-lookup"><span data-stu-id="45512-214">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="45512-215">`Enum` Deklarace obsahuje <xref:System.FlagsAttribute> atribut, který označuje, že výčtu lze považovat za sada příznaků.</span><span class="sxs-lookup"><span data-stu-id="45512-215">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>  
  
 [!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="45512-216">Příklad</span><span class="sxs-lookup"><span data-stu-id="45512-216">Example</span></span>  
 <span data-ttu-id="45512-217">Následující příklad provede iteraci výčet.</span><span class="sxs-lookup"><span data-stu-id="45512-217">The following example iterates through an enumeration.</span></span> <span data-ttu-id="45512-218">Používá <xref:System.Enum.GetNames%2A> metody k načtení pole názvy členů výčtu, a <xref:System.Enum.GetValues%2A> k načtení pole hodnoty členů.</span><span class="sxs-lookup"><span data-stu-id="45512-218">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>  
  
 [!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]  
  
## <a name="see-also"></a><span data-ttu-id="45512-219">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45512-219">See also</span></span>
- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [<span data-ttu-id="45512-220">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="45512-220">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="45512-221">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="45512-221">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="45512-222">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="45512-222">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="45512-223">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="45512-223">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="45512-224">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="45512-224">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)
