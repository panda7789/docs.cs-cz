---
title: Určení úplných názvů typů
ms.date: 02/21/2019
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- reflection, fully qualified type names
- names [.NET Framework], assemblies
- tokens
- BNF
- assemblies [.NET Framework], names
- languages, grammar
- fully qualified type names
- type names
- special characters
- IDENTIFIER
ms.assetid: d90b1e39-9115-4f2a-81c0-05e7e74e5580
ms.openlocfilehash: 707c71482196d789ed9a88db34af048ec57734fb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130030"
---
# <a name="specifying-fully-qualified-type-names"></a><span data-ttu-id="e3c1c-102">Určení plně kvalifikovaných názvů typů</span><span class="sxs-lookup"><span data-stu-id="e3c1c-102">Specifying fully qualified type names</span></span>

<span data-ttu-id="e3c1c-103">Je nutné zadat názvy typů, aby měly platný vstup k různým operacím reflexe.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-103">You must specify type names to have valid input to various reflection operations.</span></span> <span data-ttu-id="e3c1c-104">Plně kvalifikovaný název typu se skládá ze specifikace názvu sestavení, specifikace oboru názvů a názvu typu.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-104">A fully qualified type name consists of an assembly name specification, a namespace specification, and a type name.</span></span> <span data-ttu-id="e3c1c-105">Specifikace názvu typu jsou používány metodami, jako jsou <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>a <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-105">Type name specifications are used by methods such as <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, and <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span></span>

## <a name="grammar-for-type-names"></a><span data-ttu-id="e3c1c-106">Gramatika pro názvy typů</span><span class="sxs-lookup"><span data-stu-id="e3c1c-106">Grammar for type names</span></span>

 <span data-ttu-id="e3c1c-107">Gramatika definuje syntaxi formálních jazyků.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-107">The grammar defines the syntax of formal languages.</span></span> <span data-ttu-id="e3c1c-108">V následující tabulce jsou uvedeny lexikální pravidla, která popisují, jak rozpoznat platný vstup.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-108">The following table lists lexical rules that describe how to recognize a valid input.</span></span> <span data-ttu-id="e3c1c-109">Terminály (tyto prvky, které nejsou další redukovatelné) jsou uvedeny velkými písmeny.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-109">Terminals (those elements that are not further reducible) are shown in all uppercase letters.</span></span> <span data-ttu-id="e3c1c-110">Neterminály (tyto prvky, které jsou dále redukovatelné) jsou zobrazeny v kombinovaných nebo jednotlivě citovaných řetězcích, ale jednoduché uvozovky (') nejsou součástí samotné syntaxe.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-110">Nonterminals (those elements that are further reducible) are shown in mixed-case or singly quoted strings, but the single quote (') is not a part of the syntax itself.</span></span> <span data-ttu-id="e3c1c-111">Znak kanálu (&#124;) označuje pravidla, která mají podpravidla.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-111">The pipe character (&#124;) denotes rules that have subrules.</span></span>

<!-- markdownlint-disable MD010 -->
```antlr
TypeSpec
    : ReferenceTypeSpec
    | SimpleTypeSpec
    ;

ReferenceTypeSpec
    : SimpleTypeSpec '&'
    ;

SimpleTypeSpec
    : PointerTypeSpec
    | GenericTypeSpec
    | TypeName
    ;

GenericTypeSpec
   : SimpleTypeSpec ` NUMBER

PointerTypeSpec
    : SimpleTypeSpec '*'
    ;

ArrayTypeSpec
    : SimpleTypeSpec '[ReflectionDimension]'
    | SimpleTypeSpec '[ReflectionEmitDimension]'
    ;

ReflectionDimension
    : '*'
    | ReflectionDimension ',' ReflectionDimension
    | NOTOKEN
    ;

ReflectionEmitDimension
    : '*'
    | Number '..' Number
    | Number '…'
    | ReflectionDimension ',' ReflectionDimension
    | NOTOKEN
    ;

Number
    : [0-9]+
    ;

TypeName
    : NamespaceTypeName
    | NamespaceTypeName ',' AssemblyNameSpec
    ;

NamespaceTypeName
    : NestedTypeName
    | NamespaceSpec '.' NestedTypeName
    ;

NestedTypeName
    : IDENTIFIER
    | NestedTypeName '+' IDENTIFIER
    ;

NamespaceSpec
    : IDENTIFIER
    | NamespaceSpec '.' IDENTIFIER
    ;

AssemblyNameSpec
    : IDENTIFIER
    | IDENTIFIER ',' AssemblyProperties
    ;

AssemblyProperties
    : AssemblyProperty
    | AssemblyProperties ',' AssemblyProperty
    ;

AssemblyProperty
    : AssemblyPropertyName '=' AssemblyPropertyValue
    ;
```
<!-- markdownlint-enable MD010 -->

## <a name="specifying-special-characters"></a><span data-ttu-id="e3c1c-112">Určení speciálních znaků</span><span class="sxs-lookup"><span data-stu-id="e3c1c-112">Specifying special characters</span></span>

<span data-ttu-id="e3c1c-113">V názvu typu je identifikátor libovolný platný název určený pravidly jazyka.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-113">In a type name, IDENTIFIER is any valid name determined by the rules of a language.</span></span>

<span data-ttu-id="e3c1c-114">Použijte zpětné lomítko (\\) jako řídicí znak pro oddělení následujících tokenů při použití jako součást IDENTIFIKÁTORu.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-114">Use the backslash (\\) as an escape character to separate the following tokens when used as part of IDENTIFIER.</span></span>

|<span data-ttu-id="e3c1c-115">Klíčové</span><span class="sxs-lookup"><span data-stu-id="e3c1c-115">Token</span></span>|<span data-ttu-id="e3c1c-116">Význam</span><span class="sxs-lookup"><span data-stu-id="e3c1c-116">Meaning</span></span>|
|-----------|-------------|
|<span data-ttu-id="e3c1c-117">\\,</span><span class="sxs-lookup"><span data-stu-id="e3c1c-117">\\,</span></span>|<span data-ttu-id="e3c1c-118">Oddělovač sestavení</span><span class="sxs-lookup"><span data-stu-id="e3c1c-118">Assembly separator.</span></span>|
|\\+|<span data-ttu-id="e3c1c-119">Oddělovač vloženého typu</span><span class="sxs-lookup"><span data-stu-id="e3c1c-119">Nested type separator.</span></span>|
|\\&|<span data-ttu-id="e3c1c-120">Odkazový typ</span><span class="sxs-lookup"><span data-stu-id="e3c1c-120">Reference type.</span></span>|
|\\*|<span data-ttu-id="e3c1c-121">Typ ukazatele.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-121">Pointer type.</span></span>|
|<span data-ttu-id="e3c1c-122">\\[</span><span class="sxs-lookup"><span data-stu-id="e3c1c-122">\\[</span></span>|<span data-ttu-id="e3c1c-123">Oddělovač dimenze pole.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-123">Array dimension delimiter.</span></span>|
|<span data-ttu-id="e3c1c-124">\\]</span><span class="sxs-lookup"><span data-stu-id="e3c1c-124">\\]</span></span>|<span data-ttu-id="e3c1c-125">Oddělovač dimenze pole.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-125">Array dimension delimiter.</span></span>|
|<span data-ttu-id="e3c1c-126">\\.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-126">\\.</span></span>|<span data-ttu-id="e3c1c-127">Použití zpětného lomítka před tečkou pouze v případě, že se období používá ve specifikaci pole.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-127">Use the backslash before a period only if the period is used in an array specification.</span></span> <span data-ttu-id="e3c1c-128">Období v NamespaceSpec neberou zpětné lomítko.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-128">Periods in NamespaceSpec do not take the backslash.</span></span>|
|<span data-ttu-id="e3c1c-129">v případě potřeby \\\|zpětného lomítka jako řetězcový literál.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-129">\\\|Backslash when needed as a string literal.</span></span>|

<span data-ttu-id="e3c1c-130">Všimněte si, že ve všech součástech token TypeSpec s výjimkou AssemblyNameSpec jsou mezery relevantní.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-130">Note that in all TypeSpec components except AssemblyNameSpec, spaces are relevant.</span></span> <span data-ttu-id="e3c1c-131">V AssemblyNameSpec mezery před oddělovačem ', ' jsou relevantní, ale mezery za oddělovačem ', ' budou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-131">In the AssemblyNameSpec, spaces before the ',' separator are relevant, but spaces after the ',' separator are ignored.</span></span>

<span data-ttu-id="e3c1c-132">Třídy reflexe, jako je například <xref:System.Type.FullName%2A?displayProperty=nameWithType>, vrátí název pozměněný tak, aby se vrácený název mohl použít při volání <xref:System.Type.GetType%2A>, jako v `MyType.GetType(myType.FullName)`.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-132">Reflection classes, such as <xref:System.Type.FullName%2A?displayProperty=nameWithType>, return the mangled name so that the returned name can be used in a call to <xref:System.Type.GetType%2A>, as in `MyType.GetType(myType.FullName)`.</span></span>

<span data-ttu-id="e3c1c-133">Například plně kvalifikovaný název pro typ může být `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-133">For example, the fully qualified name for a type might be `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span></span>

<span data-ttu-id="e3c1c-134">Pokud byl obor názvů `Ozzy.Out+Back`, před znaménkem znaménka musí být uvozen zpětným lomítkem.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-134">If the namespace were `Ozzy.Out+Back`, then the plus sign must be preceded by a backslash.</span></span> <span data-ttu-id="e3c1c-135">V opačném případě analyzátor by ho interpretoval jako oddělovač vnořování.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-135">Otherwise, the parser would interpret it as a nesting separator.</span></span> <span data-ttu-id="e3c1c-136">Reflexe generuje tento řetězec jako `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-136">Reflection emits this string as `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span></span>

## <a name="specifying-assembly-names"></a><span data-ttu-id="e3c1c-137">Určení názvů sestavení</span><span class="sxs-lookup"><span data-stu-id="e3c1c-137">Specifying assembly names</span></span>

<span data-ttu-id="e3c1c-138">Minimální informace požadované ve specifikaci názvu sestavení jsou textový název (identifikátor) sestavení.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-138">The minimum information required in an assembly name specification is the textual name (IDENTIFIER) of the assembly.</span></span> <span data-ttu-id="e3c1c-139">Identifikátor můžete sledovat pomocí čárkami oddělený seznam párů vlastnost/hodnota, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-139">You can follow the IDENTIFIER by a comma-separated list of property/value pairs as described in the following table.</span></span> <span data-ttu-id="e3c1c-140">Názvy IDENTIFIKÁTORů by měly splňovat pravidla pro pojmenovávání souborů.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-140">IDENTIFIER naming should follow the rules for file naming.</span></span> <span data-ttu-id="e3c1c-141">V IDENTIFIKÁTORu se nerozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-141">The IDENTIFIER is case-insensitive.</span></span>

|<span data-ttu-id="e3c1c-142">Název vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e3c1c-142">Property name</span></span>|<span data-ttu-id="e3c1c-143">Popis</span><span class="sxs-lookup"><span data-stu-id="e3c1c-143">Description</span></span>|<span data-ttu-id="e3c1c-144">Povolené hodnoty</span><span class="sxs-lookup"><span data-stu-id="e3c1c-144">Allowable values</span></span>|
|-------------------|-----------------|----------------------|
|<span data-ttu-id="e3c1c-145">**Verze**</span><span class="sxs-lookup"><span data-stu-id="e3c1c-145">**Version**</span></span>|<span data-ttu-id="e3c1c-146">Číslo verze sestavení</span><span class="sxs-lookup"><span data-stu-id="e3c1c-146">Assembly version number</span></span>|<span data-ttu-id="e3c1c-147">*Hlavní_verze. podverze. sestavení. revize*, kde *hlavní*, *vedlejší*, *sestavení*a *Revize* jsou celá čísla mezi 0 a 65535 včetně.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-147">*Major.Minor.Build.Revision*, where *Major*, *Minor*, *Build*, and *Revision* are integers between 0 and 65535 inclusive.</span></span>|
|<span data-ttu-id="e3c1c-148">**PublicKey**</span><span class="sxs-lookup"><span data-stu-id="e3c1c-148">**PublicKey**</span></span>|<span data-ttu-id="e3c1c-149">Úplný veřejný klíč</span><span class="sxs-lookup"><span data-stu-id="e3c1c-149">Full public key</span></span>|<span data-ttu-id="e3c1c-150">Řetězcová hodnota úplného veřejného klíče v šestnáctkovém formátu</span><span class="sxs-lookup"><span data-stu-id="e3c1c-150">String value of full public key in hexadecimal format.</span></span> <span data-ttu-id="e3c1c-151">Zadejte nulový odkaz (**Nothing** v Visual Basic) k explicitnímu označení soukromého sestavení.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-151">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="e3c1c-152">**PublicKeyToken**</span><span class="sxs-lookup"><span data-stu-id="e3c1c-152">**PublicKeyToken**</span></span>|<span data-ttu-id="e3c1c-153">Token veřejného klíče (8bitové bajtové hodnoty hash úplného veřejného klíče)</span><span class="sxs-lookup"><span data-stu-id="e3c1c-153">Public key token (8-byte hash of the full public key)</span></span>|<span data-ttu-id="e3c1c-154">Řetězcová hodnota tokenu veřejného klíče v šestnáctkovém formátu.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-154">String value of public key token in hexadecimal format.</span></span> <span data-ttu-id="e3c1c-155">Zadejte nulový odkaz (**Nothing** v Visual Basic) k explicitnímu označení soukromého sestavení.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-155">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="e3c1c-156">**Jazykových**</span><span class="sxs-lookup"><span data-stu-id="e3c1c-156">**Culture**</span></span>|<span data-ttu-id="e3c1c-157">Jazyková verze sestavení</span><span class="sxs-lookup"><span data-stu-id="e3c1c-157">Assembly culture</span></span>|<span data-ttu-id="e3c1c-158">Jazyková verze sestavení ve formátu RFC-1766 nebo neutrální pro sestavení nezávislá na jazyce (nesatelitní).</span><span class="sxs-lookup"><span data-stu-id="e3c1c-158">Culture of the assembly in RFC-1766 format, or "neutral" for language-independent (nonsatellite) assemblies.</span></span>|
|<span data-ttu-id="e3c1c-159">**Uživatelská**</span><span class="sxs-lookup"><span data-stu-id="e3c1c-159">**Custom**</span></span>|<span data-ttu-id="e3c1c-160">Vlastní binární rozsáhlý objekt (BLOB).</span><span class="sxs-lookup"><span data-stu-id="e3c1c-160">Custom binary large object (BLOB).</span></span> <span data-ttu-id="e3c1c-161">Tato operace je aktuálně používána pouze v sestaveních generovaných [generátorem nativních bitových kopií (NGen)](../tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="e3c1c-161">This is currently used only in assemblies generated by the [Native Image Generator (Ngen)](../tools/ngen-exe-native-image-generator.md).</span></span>|<span data-ttu-id="e3c1c-162">Vlastní řetězec používaný nástrojem generátor nativních bitových kopií pro oznamování mezipaměti sestavení, že sestavení, které se instaluje, je nativní bitová kopie, a proto je nutné ji nainstalovat do mezipaměti nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-162">Custom string used by the Native Image Generator tool to notify the assembly cache that the assembly being installed is a native image, and is therefore to be installed in the native image cache.</span></span> <span data-ttu-id="e3c1c-163">Označuje se také jako řetězec zap.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-163">Also called a zap string.</span></span>|

<span data-ttu-id="e3c1c-164">Následující příklad ukazuje rozhraní **AssemblyName** pro jednoduše pojmenované sestavení s výchozí jazykovou verzí.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-164">The following example shows an **AssemblyName** for a simply named assembly with default culture.</span></span>

```csharp
com.microsoft.crypto, Culture=""
```

<span data-ttu-id="e3c1c-165">Následující příklad ukazuje plně určený odkaz pro silně pojmenované sestavení s jazykovou verzí "en".</span><span class="sxs-lookup"><span data-stu-id="e3c1c-165">The following example shows a fully specified reference for a strongly named assembly with culture "en".</span></span>

```csharp
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

<span data-ttu-id="e3c1c-166">Následující příklady každý ukazují částečně určené pole **AssemblyName**, které může být splněno buď silným, nebo jednoduše pojmenovaným sestavením.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-166">The following examples each show a partially specified **AssemblyName**, which can be satisfied by either a strong or a simply named assembly.</span></span>

```csharp
com.microsoft.crypto
com.microsoft.crypto, Culture=""
com.microsoft.crypto, Culture=en
```

<span data-ttu-id="e3c1c-167">Následující příklady každý znázorňují částečně určený **AssemblyName**, který musí být splněn jednoduše pojmenovaným sestavením.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-167">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a simply named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=null
com.microsoft.crypto, Culture=en, PublicKeyToken=null
```

<span data-ttu-id="e3c1c-168">V následujících příkladech je každý z nich zobrazen částečně určený **AssemblyName**, který musí být splněn silně pojmenovaným sestavením.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-168">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a strongly named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

## <a name="specifying-generic-types"></a><span data-ttu-id="e3c1c-169">Určení obecných typů</span><span class="sxs-lookup"><span data-stu-id="e3c1c-169">Specifying generic types</span></span>

<span data-ttu-id="e3c1c-170">SimpleTypeSpec\`číslo představuje otevřený obecný typ s parametry od 1 do *n* parametrů obecného typu.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-170">SimpleTypeSpec\`NUMBER represents an open generic type with from 1 to *n* generic type parameters.</span></span> <span data-ttu-id="e3c1c-171">Chcete-li například získat odkaz na otevřený seznam obecných typů\<T > nebo uzavřený seznam obecných typů\<> řetězce, použijte ``Type.GetType("System.Collections.Generic.List`1")`` k získání odkazu na slovník obecného typu\<TKey, TValue > , použijte ``Type.GetType("System.Collections.Generic.Dictionary`2")``.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-171">For example, to get reference to the open generic type List\<T> or the closed generic type List\<String>, use ``Type.GetType("System.Collections.Generic.List`1")`` To get a reference to the generic type Dictionary\<TKey,TValue>, use ``Type.GetType("System.Collections.Generic.Dictionary`2")``.</span></span>

## <a name="specifying-pointers"></a><span data-ttu-id="e3c1c-172">Určení ukazatelů</span><span class="sxs-lookup"><span data-stu-id="e3c1c-172">Specifying pointers</span></span>

<span data-ttu-id="e3c1c-173">SimpleTypeSpec \* představuje nespravovaný ukazatel.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-173">SimpleTypeSpec\* represents an unmanaged pointer.</span></span> <span data-ttu-id="e3c1c-174">Například chcete-li získat ukazatel na typ MyType, použijte `Type.GetType("MyType*")`.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-174">For example, to get a pointer to type MyType, use `Type.GetType("MyType*")`.</span></span> <span data-ttu-id="e3c1c-175">Chcete-li získat ukazatel na ukazatel na typ MyType, použijte `Type.GetType("MyType**")`.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-175">To get a pointer to a pointer to type MyType, use `Type.GetType("MyType**")`.</span></span>

## <a name="specifying-references"></a><span data-ttu-id="e3c1c-176">Zadání odkazů</span><span class="sxs-lookup"><span data-stu-id="e3c1c-176">Specifying references</span></span>

<span data-ttu-id="e3c1c-177">SimpleTypeSpec & představuje spravovaný ukazatel nebo odkaz.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-177">SimpleTypeSpec & represents a managed pointer or reference.</span></span> <span data-ttu-id="e3c1c-178">Například pro získání odkazu na typ MyType použijte `Type.GetType("MyType &")`.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-178">For example, to get a reference to type MyType, use `Type.GetType("MyType &")`.</span></span> <span data-ttu-id="e3c1c-179">Všimněte si, že na rozdíl od ukazatelů jsou odkazy omezeny na jednu úroveň.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-179">Note that unlike pointers, references are limited to one level.</span></span>

## <a name="specifying-arrays"></a><span data-ttu-id="e3c1c-180">Určení polí</span><span class="sxs-lookup"><span data-stu-id="e3c1c-180">Specifying arrays</span></span>

<span data-ttu-id="e3c1c-181">V BNF gramatice se ReflectionEmitDimension vztahuje pouze na neúplné definice typu načtené pomocí <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-181">In the BNF Grammar, ReflectionEmitDimension only applies to incomplete type definitions retrieved using <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e3c1c-182">Neúplné definice typu jsou <xref:System.Reflection.Emit.TypeBuilder> objekty vytvořené pomocí <xref:System.Reflection.Emit?displayProperty=nameWithType>, ale na kterých <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> nebyl volán.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-182">Incomplete type definitions are <xref:System.Reflection.Emit.TypeBuilder> objects constructed using <xref:System.Reflection.Emit?displayProperty=nameWithType> but on which <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> has not been called.</span></span> <span data-ttu-id="e3c1c-183">ReflectionDimension lze použít k načtení jakékoli definice typu, která byla dokončena, tedy typu, který byl načten.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-183">ReflectionDimension can be used to retrieve any type definition that has been completed, that is, a type that has been loaded.</span></span>

<span data-ttu-id="e3c1c-184">Pole jsou k dispozici v reflexi zadáním pořadí pole:</span><span class="sxs-lookup"><span data-stu-id="e3c1c-184">Arrays are accessed in reflection by specifying the rank of the array:</span></span>

- <span data-ttu-id="e3c1c-185">`Type.GetType("MyArray[]")` získá pole s jednou dimenzí s 0 s dolní hranicí.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-185">`Type.GetType("MyArray[]")` gets a single-dimension array with 0 lower bound.</span></span>

- <span data-ttu-id="e3c1c-186">`Type.GetType("MyArray[*]")` získá pole s jednou dimenzí, které má neznámou dolní mez.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-186">`Type.GetType("MyArray[*]")` gets a single-dimension array with unknown lower bound.</span></span>
- <span data-ttu-id="e3c1c-187">`Type.GetType("MyArray[][]")` získá pole dvourozměrného pole.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-187">`Type.GetType("MyArray[][]")` gets a two-dimensional array's array.</span></span>

- <span data-ttu-id="e3c1c-188">`Type.GetType("MyArray[*,*]")` a `Type.GetType("MyArray[,]")` získá obdélníkové dvourozměrné pole s neznámými dolními mezemi.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-188">`Type.GetType("MyArray[*,*]")` and `Type.GetType("MyArray[,]")` gets a rectangular two-dimensional array with unknown lower bounds.</span></span>

<span data-ttu-id="e3c1c-189">Všimněte si, že z běhového bodu zobrazení, `MyArray[] != MyArray[*]`, ale u multidimenzionálních polí jsou oba zápisy ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-189">Note that from a runtime point of view, `MyArray[] != MyArray[*]`, but for multidimensional arrays, the two notations are equivalent.</span></span> <span data-ttu-id="e3c1c-190">To znamená, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` se vyhodnotí jako **true**.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-190">That is, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` evaluates to **true**.</span></span>

<span data-ttu-id="e3c1c-191">Pro **modul ModuleBuilder. GetType**`MyArray[0..5]` označuje pole s jednou dimenzí, které má velikost 6, dolní mez 0.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-191">For **ModuleBuilder.GetType**, `MyArray[0..5]` indicates a single-dimension array with size 6, lower bound 0.</span></span> <span data-ttu-id="e3c1c-192">`MyArray[4…]` označuje pole s jednou dimenzí s neznámou velikostí a dolní mez 4.</span><span class="sxs-lookup"><span data-stu-id="e3c1c-192">`MyArray[4…]` indicates a single-dimension array of unknown size and lower bound 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3c1c-193">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3c1c-193">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- <xref:System.Reflection.Emit.ModuleBuilder>
- <xref:System.Reflection.Emit.TypeBuilder>
- <xref:System.Type.FullName%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e3c1c-194">Zobrazení informací o typu</span><span class="sxs-lookup"><span data-stu-id="e3c1c-194">Viewing Type Information</span></span>](viewing-type-information.md)
