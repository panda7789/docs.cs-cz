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
ms.openlocfilehash: 7cac4d5bde9ec617a1877a0605dc6dbab67ddf7f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234013"
---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="0b3b9-102">Enum – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b3b9-102">Enum Statement (Visual Basic)</span></span>
<span data-ttu-id="0b3b9-103">Výčet deklaruje a definuje hodnoty její členy.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-103">Declares an enumeration and defines the values of its members.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b3b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b3b9-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a><span data-ttu-id="0b3b9-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="0b3b9-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="0b3b9-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-106">Optional.</span></span> <span data-ttu-id="0b3b9-107">Seznam atributů, které platí pro tento výčet.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-107">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="0b3b9-108">Je nutné uzavřít [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) v lomených závorkách ("`<`"a"`>`").</span><span class="sxs-lookup"><span data-stu-id="0b3b9-108">You must enclose the [attribute list](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
     <span data-ttu-id="0b3b9-109"><xref:System.FlagsAttribute> Atribut uvádí, že hodnota instance výčtu může obsahovat více členy výčtu a aby každý člen představuje pole bit v hodnota výčtu.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="0b3b9-110">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-110">Optional.</span></span> <span data-ttu-id="0b3b9-111">Určuje, jaký kód můžete přístup tento výčet.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-111">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="0b3b9-112">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="0b3b9-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="0b3b9-113">Public</span><span class="sxs-lookup"><span data-stu-id="0b3b9-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="0b3b9-114">Protected</span><span class="sxs-lookup"><span data-stu-id="0b3b9-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="0b3b9-115">Friend</span><span class="sxs-lookup"><span data-stu-id="0b3b9-115">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="0b3b9-116">Private</span><span class="sxs-lookup"><span data-stu-id="0b3b9-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [<span data-ttu-id="0b3b9-117">Chráněné Friend</span><span class="sxs-lookup"><span data-stu-id="0b3b9-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)
    
    - [<span data-ttu-id="0b3b9-118">Privátní chráněný</span><span class="sxs-lookup"><span data-stu-id="0b3b9-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

-   `Shadows`  
  
     <span data-ttu-id="0b3b9-119">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-119">Optional.</span></span> <span data-ttu-id="0b3b9-120">Určuje, že tento výčet redeclares a skryje stejně jako s názvem programovací prvek, nebo sadu přetížené elementů v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-120">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="0b3b9-121">Můžete zadat [stínů](../../../visual-basic/language-reference/modifiers/shadows.md) pouze na daný výčet, nikoli na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-121">You can specify [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>  
  
-   `enumerationname`  
  
     <span data-ttu-id="0b3b9-122">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-122">Required.</span></span> <span data-ttu-id="0b3b9-123">Název výčtu.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-123">Name of the enumeration.</span></span> <span data-ttu-id="0b3b9-124">Informace na platné názvy najdete v tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="0b3b9-124">For information on valid names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `datatype`  
  
     <span data-ttu-id="0b3b9-125">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-125">Optional.</span></span> <span data-ttu-id="0b3b9-126">Datový typ výčtu a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-126">Data type of the enumeration and all its members.</span></span>  
  
-   `memberlist`  
  
     <span data-ttu-id="0b3b9-127">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-127">Required.</span></span> <span data-ttu-id="0b3b9-128">Seznam členů konstanty se deklarované v tomto příkazu.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-128">List of member constants being declared in this statement.</span></span> <span data-ttu-id="0b3b9-129">Na jednotlivé zdrojové řádky kódu se zobrazí více členů.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-129">Multiple members appear on individual source code lines.</span></span>  
  
     <span data-ttu-id="0b3b9-130">Každý `member` má následující syntaxe a částí: `[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="0b3b9-130">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="0b3b9-131">Část</span><span class="sxs-lookup"><span data-stu-id="0b3b9-131">Part</span></span>|<span data-ttu-id="0b3b9-132">Popis</span><span class="sxs-lookup"><span data-stu-id="0b3b9-132">Description</span></span>|  
    |---|---|  
    |`membername`|<span data-ttu-id="0b3b9-133">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-133">Required.</span></span> <span data-ttu-id="0b3b9-134">Název tohoto člena.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-134">Name of this member.</span></span>|  
    |`initializer`|<span data-ttu-id="0b3b9-135">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-135">Optional.</span></span> <span data-ttu-id="0b3b9-136">Výraz, který se vyhodnotí v době kompilace a přiřadí do tohoto člena.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-136">Expression that is evaluated at compile time and assigned to this member.</span></span>|  
  
-   <span data-ttu-id="0b3b9-137">`End``Enum`</span><span class="sxs-lookup"><span data-stu-id="0b3b9-137">`End` `Enum`</span></span>  
  
     <span data-ttu-id="0b3b9-138">Ukončí `Enum` bloku.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-138">Terminates the `Enum` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b3b9-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b3b9-139">Remarks</span></span>  
 <span data-ttu-id="0b3b9-140">Pokud máte sadu neměnné hodnoty, které jsou logicky vzájemně souvisí, můžete je definovat společně ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-140">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="0b3b9-141">To umožňuje smysluplné názvy pro výčet a její členy, které se snadněji mějte na paměti, než jejich hodnot.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-141">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="0b3b9-142">Potom můžete členy výčtu na mnoha místech v kódu.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-142">You can then use the enumeration members in many places in your code.</span></span>  
  
 <span data-ttu-id="0b3b9-143">Výhody použití výčty patří:</span><span class="sxs-lookup"><span data-stu-id="0b3b9-143">The benefits of using enumerations include the following:</span></span>  
  
-   <span data-ttu-id="0b3b9-144">Snižuje chyby způsobené transpozice nebo chybným zadáním čísla.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-144">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="0b3b9-145">Lze snadno ke změně hodnot v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-145">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="0b3b9-146">Díky kód snadněji číst, což znamená, že je méně pravděpodobné, že bude nutné zavést chyb.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-146">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>  
  
-   <span data-ttu-id="0b3b9-147">Zajišťuje kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-147">Ensures forward compatibility.</span></span> <span data-ttu-id="0b3b9-148">Pokud používáte výčty, váš kód je méně pravděpodobné, že nezdaří, pokud v budoucnu někdo změní hodnoty odpovídající názvy členů.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-148">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
 <span data-ttu-id="0b3b9-149">Výčet má název, základní datový typ a sadu členů.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-149">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="0b3b9-150">Každý člen představuje konstantu.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-150">Each member represents a constant.</span></span>  
  
 <span data-ttu-id="0b3b9-151">Výčet deklarovat na třídy, struktury, modul nebo úroveň rozhraní mimo libovolná procedura je *člen výčtu*.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-151">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="0b3b9-152">Je členem třídy, struktury, modul nebo rozhraní, který deklaruje ho.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-152">It is a member of the class, structure, module, or interface that declares it.</span></span>  
  
 <span data-ttu-id="0b3b9-153">Výčty člen je přístupná z kdekoli v rámci třídy, struktury, modul nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-153">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="0b3b9-154">Kód mimo třída, struktura nebo modul kvalifikaci název člena výčtu s názvem třídy, struktury nebo modul.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-154">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="0b3b9-155">Nutnost používat plně kvalifikované názvy přidáním se můžete vyhnout [importy](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) příkaz ke zdrojovému souboru.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-155">You can avoid the need to use fully qualified names by adding an [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>  
  
 <span data-ttu-id="0b3b9-156">Výčet deklarovat na úrovni oboru názvů, mimo třídy, struktury, modul nebo rozhraní, je členem oboru názvů, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-156">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>  
  
 <span data-ttu-id="0b3b9-157">*Deklarace kontextu* pro výčet musí být zdrojový soubor, obor názvů, třídy, struktury, modul nebo rozhraní a nemůže být procedury.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-157">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="0b3b9-158">Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0b3b9-158">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="0b3b9-159">Můžete použít atributy výčet jako celek, ale ne její členové jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-159">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="0b3b9-160">Atribut přispívá informace metadat sestavení.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-160">An attribute contributes information to the assembly's metadata.</span></span>  
  
## <a name="data-type"></a><span data-ttu-id="0b3b9-161">Datový typ</span><span class="sxs-lookup"><span data-stu-id="0b3b9-161">Data Type</span></span>  
 <span data-ttu-id="0b3b9-162">`Enum` Příkaz můžou deklarovat datový typ výčtu.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-162">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="0b3b9-163">Každý člen má datový typ výčtu.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-163">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="0b3b9-164">Můžete zadat `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, nebo `UShort`.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-164">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>  
  
 <span data-ttu-id="0b3b9-165">Pokud nezadáte `datatype` pro výčet, každý člen má datový typ jeho `initializer`.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-165">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="0b3b9-166">Pokud zadáte oba `datatype` a `initializer`, datový typ `initializer` musí být převoditelná na `datatype`.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-166">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="0b3b9-167">Pokud ani `datatype` ani `initializer` je k dispozici, výchozí hodnota je typu dat `Integer`.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-167">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>  
  
## <a name="initializing-members"></a><span data-ttu-id="0b3b9-168">Inicializace členů</span><span class="sxs-lookup"><span data-stu-id="0b3b9-168">Initializing Members</span></span>  
 <span data-ttu-id="0b3b9-169">`Enum` Příkaz můžete inicializovat obsah vybrané členy v `memberlist`.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-169">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="0b3b9-170">Používáte `initializer` k poskytování výraz přiřazení člena.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-170">You use `initializer` to supply an expression to be assigned to the member.</span></span>  
  
 <span data-ttu-id="0b3b9-171">Pokud nezadáte `initializer` pro člena, Visual Basic inicializuje se buď na nulu (Pokud je první `member` v `memberlist`), nebo k hodnotě větší, jedna než bezprostředně před `member`.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-171">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>  
  
 <span data-ttu-id="0b3b9-172">Výraz zadaný v každé `initializer` může být libovolnou kombinací literály, ostatní konstanty, které jsou již definováni a členové výčtu, které jsou již definováni, včetně předchozí členem tento výčet.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-172">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="0b3b9-173">Aritmetické a logické operátory můžete kombinovat takové elementy.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-173">You can use arithmetic and logical operators to combine such elements.</span></span>  
  
 <span data-ttu-id="0b3b9-174">Nemůžete použít proměnné nebo funkce v `initializer`.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-174">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="0b3b9-175">Nicméně můžete používat klíčová slova převodu jako třeba `CByte` a `CShort`.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-175">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="0b3b9-176">Můžete také použít `AscW` při volání s konstantní `String` nebo `Char` argument, vzhledem k tomu, který lze vyhodnotit v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-176">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>  
  
 <span data-ttu-id="0b3b9-177">Výčty nesmí mít hodnoty s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-177">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="0b3b9-178">Pokud je členem přiřadit hodnotu s plovoucí desetinnou čárkou a `Option Strict` nastavená na on, dojde k chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-178">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="0b3b9-179">Pokud `Option Strict` je vypnutý, hodnota je automaticky převeden na `Enum` typu.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-179">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="0b3b9-180">Pokud hodnotu člena překračuje povolený rozsah pro základní datový typ, nebo pokud inicializovat kteréhokoli člena maximální hodnotě povolené základní datový typ, kompilátor ohlásí chybu.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-180">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>  
  
## <a name="modifiers"></a><span data-ttu-id="0b3b9-181">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="0b3b9-181">Modifiers</span></span>  
 <span data-ttu-id="0b3b9-182">Třída, struktura, modulu a rozhraní člen výčty výchozí nastavení veřejný přístup.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-182">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="0b3b9-183">Můžete nastavit jejich úrovně přístupu s modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-183">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="0b3b9-184">Namespace člen výčty výchozí friend přístupu.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-184">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="0b3b9-185">Můžete nastavit jejich úrovně přístupu na veřejné, ale ne na soukromé nebo chráněné.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-185">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="0b3b9-186">Další informace najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0b3b9-186">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="0b3b9-187">Všechny členy výčtu musejí veřejný přístup, a všechny modifikátory přístupu nelze použít na ně.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-187">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="0b3b9-188">Pokud daný výčet má omezenější úroveň přístupu, ale úroveň přístupu zadaný výčet má přednost před.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-188">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>  
  
 <span data-ttu-id="0b3b9-189">Ve výchozím nastavení všechny výčty jsou typy a jejich pole jsou konstanty.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-189">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="0b3b9-190">Proto `Shared`, `Static`, a `ReadOnly` klíčová slova nelze použít v případě deklarace výčet nebo její členy.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-190">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>  
  
## <a name="assigning-multiple-values"></a><span data-ttu-id="0b3b9-191">Přiřazení více hodnot</span><span class="sxs-lookup"><span data-stu-id="0b3b9-191">Assigning Multiple Values</span></span>  
 <span data-ttu-id="0b3b9-192">Výčty obvykle představují vzájemně se vylučuje hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-192">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="0b3b9-193">Zahrnutím <xref:System.FlagsAttribute> atribut `Enum` deklaraci, můžete místo toho přiřadit více hodnot do instance výčtu.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-193">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="0b3b9-194"><xref:System.FlagsAttribute> Atribut určuje, že výčtu být považovány za bitové pole, který je sada příznaků.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-194">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="0b3b9-195">Toto nastavení se nazývá *bitové* výčty.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-195">These are called *bitwise* enumerations.</span></span>  
  
 <span data-ttu-id="0b3b9-196">Když pomocí deklarace výčtů <xref:System.FlagsAttribute> atribut, doporučujeme, abyste používali zajišťuje 2, který je, 1, 2, 4, 8, 16 a tak dále, pro hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-196">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="0b3b9-197">Doporučujeme také, že "Žádný" být název člena, jehož hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-197">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="0b3b9-198">Další pokyny najdete v části <xref:System.FlagsAttribute> a <xref:System.Enum>.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-198">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b3b9-199">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b3b9-199">Example</span></span>  
 <span data-ttu-id="0b3b9-200">Následující příklad ukazuje způsob použití `Enum` příkaz.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-200">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="0b3b9-201">Všimněte si, že člen se označuje jako `EggSizeEnum.Medium`a ne jako `Medium`.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-201">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>  
  
 [!code-vb[VbEnumsTask#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="0b3b9-202">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b3b9-202">Example</span></span>  
 <span data-ttu-id="0b3b9-203">Metoda v následujícím příkladu je mimo `Egg` třídy.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-203">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="0b3b9-204">Proto `EggSizeEnum` je plně kvalifikovaný jako `Egg.EggSizeEnum`.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-204">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>  
  
 [!code-vb[VbEnumsTask#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="0b3b9-205">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b3b9-205">Example</span></span>  
 <span data-ttu-id="0b3b9-206">Následující příklad používá `Enum` příkaz k definování související sadu s názvem konstantní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-206">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="0b3b9-207">V takovém případě hodnoty jsou barev, které můžete zvolit návrh formuláře pro zadávání dat pro databázi.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-207">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>  
  
 [!code-vb[VbEnumsTask#30](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="0b3b9-208">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b3b9-208">Example</span></span>  
 <span data-ttu-id="0b3b9-209">Následující příklad ukazuje hodnoty, které zahrnují kladné a záporné čísla.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-209">The following example shows values that include both positive and negative numbers.</span></span>  
  
 [!code-vb[VbEnumsTask#31](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="0b3b9-210">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b3b9-210">Example</span></span>  
 <span data-ttu-id="0b3b9-211">V následujícím příkladu se `As` klauzule slouží k určení `datatype` výčtu.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-211">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>  
  
 [!code-vb[VbEnumsTask#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="0b3b9-212">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b3b9-212">Example</span></span>  
 <span data-ttu-id="0b3b9-213">Následující příklad ukazuje, jak používat bitové výčet.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-213">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="0b3b9-214">Více hodnot lze přiřadit k instanci bitové výčtu.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-214">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="0b3b9-215">`Enum` Zahrnuje deklaraci <xref:System.FlagsAttribute> atribut, který označuje, že výčtu lze považovat za sadu příznaků.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-215">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>  
  
 [!code-vb[VbEnumsTask#61](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]  
  
## <a name="example"></a><span data-ttu-id="0b3b9-216">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b3b9-216">Example</span></span>  
 <span data-ttu-id="0b3b9-217">V následujícím příkladu prochází výčet.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-217">The following example iterates through an enumeration.</span></span> <span data-ttu-id="0b3b9-218">Použije <xref:System.Enum.GetNames%2A> metoda k načtení pole názvy členů z výčtu, a <xref:System.Enum.GetValues%2A> k načtení pole hodnot členů.</span><span class="sxs-lookup"><span data-stu-id="0b3b9-218">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>  
  
 [!code-vb[VbEnumsTask#51](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0b3b9-219">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b3b9-219">See Also</span></span>  
 <xref:System.Enum>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 [<span data-ttu-id="0b3b9-220">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="0b3b9-220">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="0b3b9-221">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="0b3b9-221">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="0b3b9-222">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="0b3b9-222">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="0b3b9-223">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="0b3b9-223">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="0b3b9-224">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="0b3b9-224">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)
