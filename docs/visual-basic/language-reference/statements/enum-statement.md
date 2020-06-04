---
title: Enum – příkaz
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
ms.openlocfilehash: 976cc68d67c69ec86918962ab2dd3406d15aed9a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404729"
---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="56d3c-102">Enum – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56d3c-102">Enum Statement (Visual Basic)</span></span>

<span data-ttu-id="56d3c-103">Deklaruje výčet a definuje hodnoty jeho členů.</span><span class="sxs-lookup"><span data-stu-id="56d3c-103">Declares an enumeration and defines the values of its members.</span></span>

## <a name="syntax"></a><span data-ttu-id="56d3c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56d3c-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]
Enum enumerationname [ As datatype ]
   memberlist
End Enum
```

## <a name="parts"></a><span data-ttu-id="56d3c-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="56d3c-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="56d3c-106">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="56d3c-106">Optional.</span></span> <span data-ttu-id="56d3c-107">Seznam atributů, které se vztahují k tomuto výčtu.</span><span class="sxs-lookup"><span data-stu-id="56d3c-107">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="56d3c-108">[Seznam atributů](attribute-list.md) musíte uzavřít do lomených závorek (" `<` " a " `>` ").</span><span class="sxs-lookup"><span data-stu-id="56d3c-108">You must enclose the [attribute list](attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

  <span data-ttu-id="56d3c-109"><xref:System.FlagsAttribute>Atribut označuje, že hodnota instance výčtu může zahrnovat více členů výčtu a že každý člen představuje bitové pole v hodnotě výčtu.</span><span class="sxs-lookup"><span data-stu-id="56d3c-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>

- `accessmodifier`

  <span data-ttu-id="56d3c-110">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="56d3c-110">Optional.</span></span> <span data-ttu-id="56d3c-111">Určuje, který kód má k tomuto výčtu přístup.</span><span class="sxs-lookup"><span data-stu-id="56d3c-111">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="56d3c-112">Může to být jedna z následujících:</span><span class="sxs-lookup"><span data-stu-id="56d3c-112">Can be one of the following:</span></span>

  - [<span data-ttu-id="56d3c-113">Republik</span><span class="sxs-lookup"><span data-stu-id="56d3c-113">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="56d3c-114">Proti</span><span class="sxs-lookup"><span data-stu-id="56d3c-114">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="56d3c-115">Friend</span><span class="sxs-lookup"><span data-stu-id="56d3c-115">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="56d3c-116">Hlášen</span><span class="sxs-lookup"><span data-stu-id="56d3c-116">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="56d3c-117">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="56d3c-117">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="56d3c-118">Soukromé chráněné</span><span class="sxs-lookup"><span data-stu-id="56d3c-118">Private Protected</span></span>](../modifiers/private-protected.md)

- `Shadows`

  <span data-ttu-id="56d3c-119">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="56d3c-119">Optional.</span></span> <span data-ttu-id="56d3c-120">Určuje, že tento výčet znovu deklaruje a skryje identicky pojmenovaný prvek programování nebo sadu přetížených prvků v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="56d3c-120">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="56d3c-121">[Stíny](../modifiers/shadows.md) lze zadat pouze pro samotný výčet, nikoli na žádném z jeho členů.</span><span class="sxs-lookup"><span data-stu-id="56d3c-121">You can specify [Shadows](../modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>

- `enumerationname`

  <span data-ttu-id="56d3c-122">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="56d3c-122">Required.</span></span> <span data-ttu-id="56d3c-123">Název výčtu.</span><span class="sxs-lookup"><span data-stu-id="56d3c-123">Name of the enumeration.</span></span> <span data-ttu-id="56d3c-124">Informace o platných názvech naleznete v tématu [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="56d3c-124">For information on valid names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `datatype`

  <span data-ttu-id="56d3c-125">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="56d3c-125">Optional.</span></span> <span data-ttu-id="56d3c-126">Datový typ výčtu a všech jeho členů.</span><span class="sxs-lookup"><span data-stu-id="56d3c-126">Data type of the enumeration and all its members.</span></span>

- `memberlist`

  <span data-ttu-id="56d3c-127">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="56d3c-127">Required.</span></span> <span data-ttu-id="56d3c-128">Seznam konstant členů, které jsou deklarovány v tomto příkazu.</span><span class="sxs-lookup"><span data-stu-id="56d3c-128">List of member constants being declared in this statement.</span></span> <span data-ttu-id="56d3c-129">Na jednotlivých řádcích zdrojového kódu se zobrazí více členů.</span><span class="sxs-lookup"><span data-stu-id="56d3c-129">Multiple members appear on individual source code lines.</span></span>

  <span data-ttu-id="56d3c-130">Každá `member` z nich má následující syntaxi a části:`[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="56d3c-130">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>

  |<span data-ttu-id="56d3c-131">Část</span><span class="sxs-lookup"><span data-stu-id="56d3c-131">Part</span></span>|<span data-ttu-id="56d3c-132">Description</span><span class="sxs-lookup"><span data-stu-id="56d3c-132">Description</span></span>|
  |---|---|
  |`membername`|<span data-ttu-id="56d3c-133">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="56d3c-133">Required.</span></span> <span data-ttu-id="56d3c-134">Název tohoto člena</span><span class="sxs-lookup"><span data-stu-id="56d3c-134">Name of this member.</span></span>|
  |`initializer`|<span data-ttu-id="56d3c-135">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="56d3c-135">Optional.</span></span> <span data-ttu-id="56d3c-136">Výraz, který se vyhodnocuje v době kompilace a přiřazený k tomuto členovi.</span><span class="sxs-lookup"><span data-stu-id="56d3c-136">Expression that is evaluated at compile time and assigned to this member.</span></span>|

- <span data-ttu-id="56d3c-137">`End` `Enum`</span><span class="sxs-lookup"><span data-stu-id="56d3c-137">`End` `Enum`</span></span>

  <span data-ttu-id="56d3c-138">Ukončí `Enum` blok.</span><span class="sxs-lookup"><span data-stu-id="56d3c-138">Terminates the `Enum` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="56d3c-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56d3c-139">Remarks</span></span>

<span data-ttu-id="56d3c-140">Máte-li sadu nezměněných hodnot, které jsou logicky vzájemně propojeny, můžete je definovat společně ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="56d3c-140">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="56d3c-141">To poskytuje smysluplné názvy pro výčet a jeho členy, které je snazší pamatovat než jejich hodnoty.</span><span class="sxs-lookup"><span data-stu-id="56d3c-141">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="56d3c-142">Pak můžete použít členy výčtu na mnoha místech v kódu.</span><span class="sxs-lookup"><span data-stu-id="56d3c-142">You can then use the enumeration members in many places in your code.</span></span>

<span data-ttu-id="56d3c-143">Mezi výhody používání výčtů patří následující:</span><span class="sxs-lookup"><span data-stu-id="56d3c-143">The benefits of using enumerations include the following:</span></span>

- <span data-ttu-id="56d3c-144">Snižuje chyby způsobené přetypováním nebo nesprávným zadáním čísel.</span><span class="sxs-lookup"><span data-stu-id="56d3c-144">Reduces errors caused by transposing or mistyping numbers.</span></span>

- <span data-ttu-id="56d3c-145">V budoucnu usnadňuje změnu hodnot.</span><span class="sxs-lookup"><span data-stu-id="56d3c-145">Makes it easy to change values in the future.</span></span>

- <span data-ttu-id="56d3c-146">Usnadňuje čtení kódu, což znamená, že je méně pravděpodobný, že budou zavedeny chyby.</span><span class="sxs-lookup"><span data-stu-id="56d3c-146">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>

- <span data-ttu-id="56d3c-147">Zajišťuje dopředné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="56d3c-147">Ensures forward compatibility.</span></span> <span data-ttu-id="56d3c-148">Pokud použijete výčty, váš kód je méně pravděpodobný, pokud v budoucnu někdo změní hodnoty odpovídající názvům členů.</span><span class="sxs-lookup"><span data-stu-id="56d3c-148">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>

<span data-ttu-id="56d3c-149">Výčet má název, základní datový typ a sadu členů.</span><span class="sxs-lookup"><span data-stu-id="56d3c-149">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="56d3c-150">Každý člen představuje konstantu.</span><span class="sxs-lookup"><span data-stu-id="56d3c-150">Each member represents a constant.</span></span>

<span data-ttu-id="56d3c-151">Výčet deklarovaný na úrovni třídy, struktury, modulu nebo rozhraní, mimo jakoukoli proceduru, je *výčet členů*.</span><span class="sxs-lookup"><span data-stu-id="56d3c-151">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="56d3c-152">Je členem třídy, struktury, modulu nebo rozhraní, které je deklaruje.</span><span class="sxs-lookup"><span data-stu-id="56d3c-152">It is a member of the class, structure, module, or interface that declares it.</span></span>

<span data-ttu-id="56d3c-153">K výčtům členů lze přistupovat odkudkoli v rámci své třídy, struktury, modulu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="56d3c-153">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="56d3c-154">Kód mimo třídu, strukturu nebo modul musí kvalifikovat název výčtu členů s názvem této třídy, struktury nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="56d3c-154">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="56d3c-155">Je možné vyhnout se nutnosti používat plně kvalifikované názvy přidáním příkazu [Imports](imports-statement-net-namespace-and-type.md) do zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="56d3c-155">You can avoid the need to use fully qualified names by adding an [Imports](imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>

<span data-ttu-id="56d3c-156">Výčet deklarovaný na úrovni oboru názvů, mimo jakoukoliv třídu, strukturu, modul nebo rozhraní, je členem oboru názvů, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="56d3c-156">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>

<span data-ttu-id="56d3c-157">*Kontext deklarace* pro výčet musí být zdrojový soubor, obor názvů, třída, struktura, modul nebo rozhraní a nemůže být procedura.</span><span class="sxs-lookup"><span data-stu-id="56d3c-157">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="56d3c-158">Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="56d3c-158">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="56d3c-159">Můžete použít atributy na výčet jako celek, ale nikoli na jeho členy jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="56d3c-159">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="56d3c-160">Atribut přispívá informace k metadatům sestavení.</span><span class="sxs-lookup"><span data-stu-id="56d3c-160">An attribute contributes information to the assembly's metadata.</span></span>

## <a name="data-type"></a><span data-ttu-id="56d3c-161">Typ dat</span><span class="sxs-lookup"><span data-stu-id="56d3c-161">Data Type</span></span>

<span data-ttu-id="56d3c-162">`Enum`Příkaz může deklarovat datový typ výčtu.</span><span class="sxs-lookup"><span data-stu-id="56d3c-162">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="56d3c-163">Každý člen získá datový typ výčtu.</span><span class="sxs-lookup"><span data-stu-id="56d3c-163">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="56d3c-164">Můžete zadat `Byte` , `Integer` , `Long` , `SByte` , `Short` , `UInteger` , `ULong` , nebo `UShort` .</span><span class="sxs-lookup"><span data-stu-id="56d3c-164">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>

<span data-ttu-id="56d3c-165">Pokud pro výčet neurčíte `datatype` , každý člen získá datový typ svého `initializer` .</span><span class="sxs-lookup"><span data-stu-id="56d3c-165">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="56d3c-166">Pokud zadáte obojí `datatype` a `initializer` , datový typ `initializer` musí být převoditelné na `datatype` .</span><span class="sxs-lookup"><span data-stu-id="56d3c-166">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="56d3c-167">V případě `datatype` `initializer` , že není k dispozici ani, je výchozím datovým typem `Integer` .</span><span class="sxs-lookup"><span data-stu-id="56d3c-167">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>

## <a name="initializing-members"></a><span data-ttu-id="56d3c-168">Inicializace členů</span><span class="sxs-lookup"><span data-stu-id="56d3c-168">Initializing Members</span></span>

<span data-ttu-id="56d3c-169">`Enum`Příkaz může inicializovat obsah vybraných členů v `memberlist` .</span><span class="sxs-lookup"><span data-stu-id="56d3c-169">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="56d3c-170">Použijete `initializer` k poskytnutí výrazu, který má být přiřazen členu.</span><span class="sxs-lookup"><span data-stu-id="56d3c-170">You use `initializer` to supply an expression to be assigned to the member.</span></span>

<span data-ttu-id="56d3c-171">Pokud pro člena neurčíte `initializer` , Visual Basic inicializuje buď na nulu (Pokud se jedná o první `member` v `memberlist` ), nebo na hodnotu větší od jedné, než je bezprostředně předchozí `member` .</span><span class="sxs-lookup"><span data-stu-id="56d3c-171">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>

<span data-ttu-id="56d3c-172">Výraz zadaný v každém z nich `initializer` může být libovolná kombinace literálů, dalších konstant, které jsou již definovány, a členů výčtu, kteří jsou již definováni, včetně předchozího člena tohoto výčtu.</span><span class="sxs-lookup"><span data-stu-id="56d3c-172">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="56d3c-173">K kombinování takových prvků lze použít aritmetické a logické operátory.</span><span class="sxs-lookup"><span data-stu-id="56d3c-173">You can use arithmetic and logical operators to combine such elements.</span></span>

<span data-ttu-id="56d3c-174">V nástroji nelze použít proměnné nebo funkce `initializer` .</span><span class="sxs-lookup"><span data-stu-id="56d3c-174">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="56d3c-175">Můžete však použít klíčová slova převodu, jako je `CByte` a `CShort` .</span><span class="sxs-lookup"><span data-stu-id="56d3c-175">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="56d3c-176">Můžete také použít, `AscW` Pokud je volána s konstantou `String` nebo `Char` argumentem, protože lze vyhodnotit v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="56d3c-176">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>

<span data-ttu-id="56d3c-177">Výčty nemůžou mít hodnoty s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="56d3c-177">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="56d3c-178">Pokud je členovi přiřazena hodnota s plovoucí desetinnou čárkou a `Option Strict` je nastavena na hodnotu on, dojde k chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="56d3c-178">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="56d3c-179">Pokud `Option Strict` je hodnota vypnuta, hodnota je automaticky převedena na `Enum` typ.</span><span class="sxs-lookup"><span data-stu-id="56d3c-179">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>

<span data-ttu-id="56d3c-180">Pokud hodnota členu překročí povolený rozsah pro základní datový typ, nebo Pokud inicializujete libovolného člena na maximální hodnotu povolenou podkladovým datovým typem, kompilátor ohlásí chybu.</span><span class="sxs-lookup"><span data-stu-id="56d3c-180">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>

## <a name="modifiers"></a><span data-ttu-id="56d3c-181">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="56d3c-181">Modifiers</span></span>

<span data-ttu-id="56d3c-182">Výčet členů třídy, struktury, modulu a rozhraní je ve výchozím nastavení veřejným přístupem.</span><span class="sxs-lookup"><span data-stu-id="56d3c-182">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="56d3c-183">Můžete upravit jejich úrovně přístupu modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="56d3c-183">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="56d3c-184">Výčty členů oboru názvů mají ve výchozím nastavení přístup typu Friend.</span><span class="sxs-lookup"><span data-stu-id="56d3c-184">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="56d3c-185">Úrovně přístupu můžete upravit na veřejné, ale ne na privátní nebo chráněné.</span><span class="sxs-lookup"><span data-stu-id="56d3c-185">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="56d3c-186">Další informace najdete v tématu [úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="56d3c-186">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="56d3c-187">Všichni členové výčtu mají veřejný přístup a nemůžete použít žádné modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="56d3c-187">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="56d3c-188">Nicméně pokud má výčet vlastní úroveň přístupu s vyšší úrovní oprávnění, má zadaná úroveň přístupu ke výčtu přednost.</span><span class="sxs-lookup"><span data-stu-id="56d3c-188">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>

<span data-ttu-id="56d3c-189">Ve výchozím nastavení jsou všechny výčty typy a jejich pole jsou konstanty.</span><span class="sxs-lookup"><span data-stu-id="56d3c-189">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="56d3c-190">`Shared` `Static` `ReadOnly` Klíčová slova, a nelze proto použít při deklaraci výčtu nebo jejích členů.</span><span class="sxs-lookup"><span data-stu-id="56d3c-190">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>

## <a name="assigning-multiple-values"></a><span data-ttu-id="56d3c-191">Přiřazení více hodnot</span><span class="sxs-lookup"><span data-stu-id="56d3c-191">Assigning Multiple Values</span></span>

<span data-ttu-id="56d3c-192">Výčty typicky znázorňují vzájemně se vylučující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="56d3c-192">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="56d3c-193">Zahrnutím <xref:System.FlagsAttribute> atributu do `Enum` deklarace můžete místo toho přiřadit více hodnot instanci výčtu.</span><span class="sxs-lookup"><span data-stu-id="56d3c-193">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="56d3c-194"><xref:System.FlagsAttribute>Atribut určuje, že výčet bude zpracován jako bitové pole, tedy sada příznaků.</span><span class="sxs-lookup"><span data-stu-id="56d3c-194">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="56d3c-195">Tyto jsou označovány jako *bitové* výčty.</span><span class="sxs-lookup"><span data-stu-id="56d3c-195">These are called *bitwise* enumerations.</span></span>

<span data-ttu-id="56d3c-196">Pokud deklarujete výčet pomocí <xref:System.FlagsAttribute> atributu, doporučujeme pro tyto hodnoty použít mocniny 2, to znamená 1, 2, 4, 8, 16 a tak dále.</span><span class="sxs-lookup"><span data-stu-id="56d3c-196">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="56d3c-197">Doporučujeme také, aby "žádný" byl název členu, jehož hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="56d3c-197">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="56d3c-198">Další pokyny naleznete v tématech <xref:System.FlagsAttribute> a <xref:System.Enum> .</span><span class="sxs-lookup"><span data-stu-id="56d3c-198">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>

## <a name="example"></a><span data-ttu-id="56d3c-199">Příklad</span><span class="sxs-lookup"><span data-stu-id="56d3c-199">Example</span></span>

<span data-ttu-id="56d3c-200">Následující příklad ukazuje, jak použít `Enum` příkaz.</span><span class="sxs-lookup"><span data-stu-id="56d3c-200">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="56d3c-201">Všimněte si, že člen je označován jako `EggSizeEnum.Medium` a nikoli jako `Medium` .</span><span class="sxs-lookup"><span data-stu-id="56d3c-201">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>

[!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]

## <a name="example"></a><span data-ttu-id="56d3c-202">Příklad</span><span class="sxs-lookup"><span data-stu-id="56d3c-202">Example</span></span>

<span data-ttu-id="56d3c-203">Metoda v následujícím příkladu je mimo `Egg` třídu.</span><span class="sxs-lookup"><span data-stu-id="56d3c-203">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="56d3c-204">Proto `EggSizeEnum` je plně kvalifikovaný jako `Egg.EggSizeEnum` .</span><span class="sxs-lookup"><span data-stu-id="56d3c-204">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>

[!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]

## <a name="example"></a><span data-ttu-id="56d3c-205">Příklad</span><span class="sxs-lookup"><span data-stu-id="56d3c-205">Example</span></span>

<span data-ttu-id="56d3c-206">Následující příklad používá `Enum` příkaz k definování související sady pojmenovaných hodnot konstant.</span><span class="sxs-lookup"><span data-stu-id="56d3c-206">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="56d3c-207">V tomto případě hodnoty jsou barvy, které můžete zvolit pro návrh formulářů pro zadávání dat pro databázi.</span><span class="sxs-lookup"><span data-stu-id="56d3c-207">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>

[!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]

## <a name="example"></a><span data-ttu-id="56d3c-208">Příklad</span><span class="sxs-lookup"><span data-stu-id="56d3c-208">Example</span></span>

<span data-ttu-id="56d3c-209">Následující příklad ukazuje hodnoty, které obsahují kladná i záporná čísla.</span><span class="sxs-lookup"><span data-stu-id="56d3c-209">The following example shows values that include both positive and negative numbers.</span></span>

[!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]

## <a name="example"></a><span data-ttu-id="56d3c-210">Příklad</span><span class="sxs-lookup"><span data-stu-id="56d3c-210">Example</span></span>

<span data-ttu-id="56d3c-211">V následujícím příkladu `As` je použita klauzule k určení `datatype` výčtu.</span><span class="sxs-lookup"><span data-stu-id="56d3c-211">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>

[!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]

## <a name="example"></a><span data-ttu-id="56d3c-212">Příklad</span><span class="sxs-lookup"><span data-stu-id="56d3c-212">Example</span></span>

<span data-ttu-id="56d3c-213">Následující příklad ukazuje, jak použít bitový výčet.</span><span class="sxs-lookup"><span data-stu-id="56d3c-213">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="56d3c-214">K instanci bitového výčtu lze přiřadit více hodnot.</span><span class="sxs-lookup"><span data-stu-id="56d3c-214">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="56d3c-215">`Enum`Deklarace obsahuje <xref:System.FlagsAttribute> atribut, který označuje, že výčet lze považovat za sadu příznaků.</span><span class="sxs-lookup"><span data-stu-id="56d3c-215">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>

[!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]

## <a name="example"></a><span data-ttu-id="56d3c-216">Příklad</span><span class="sxs-lookup"><span data-stu-id="56d3c-216">Example</span></span>

<span data-ttu-id="56d3c-217">Následující příklad prochází výčet.</span><span class="sxs-lookup"><span data-stu-id="56d3c-217">The following example iterates through an enumeration.</span></span> <span data-ttu-id="56d3c-218">Používá <xref:System.Enum.GetNames%2A> metodu k načtení pole názvů členů z výčtu a <xref:System.Enum.GetValues%2A> k načtení pole hodnot členů.</span><span class="sxs-lookup"><span data-stu-id="56d3c-218">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>

[!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="56d3c-219">Viz také</span><span class="sxs-lookup"><span data-stu-id="56d3c-219">See also</span></span>

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [<span data-ttu-id="56d3c-220">Const – příkaz</span><span class="sxs-lookup"><span data-stu-id="56d3c-220">Const Statement</span></span>](const-statement.md)
- [<span data-ttu-id="56d3c-221">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="56d3c-221">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="56d3c-222">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="56d3c-222">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="56d3c-223">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="56d3c-223">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="56d3c-224">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="56d3c-224">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
