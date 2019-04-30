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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc8395492992c22da3c635f0de010516127f9be4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793000"
---
# <a name="specifying-fully-qualified-type-names"></a><span data-ttu-id="fa55b-102">Určení úplných názvů typů</span><span class="sxs-lookup"><span data-stu-id="fa55b-102">Specifying fully qualified type names</span></span>

<span data-ttu-id="fa55b-103">Je nutné zadat názvy typů mít platné zadání do různých operací reflexe.</span><span class="sxs-lookup"><span data-stu-id="fa55b-103">You must specify type names to have valid input to various reflection operations.</span></span> <span data-ttu-id="fa55b-104">Plně kvalifikovaného názvu typu se skládá z specifikaci název sestavení, oboru názvů a název typu.</span><span class="sxs-lookup"><span data-stu-id="fa55b-104">A fully qualified type name consists of an assembly name specification, a namespace specification, and a type name.</span></span> <span data-ttu-id="fa55b-105">Specifikace názvu typu jsou používány metody jako například <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, a <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fa55b-105">Type name specifications are used by methods such as <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, and <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span></span>

## <a name="grammar-for-type-names"></a><span data-ttu-id="fa55b-106">Gramatika pro názvy typů</span><span class="sxs-lookup"><span data-stu-id="fa55b-106">Grammar for type names</span></span>

 <span data-ttu-id="fa55b-107">Gramatika definuje syntaxe formální jazyků.</span><span class="sxs-lookup"><span data-stu-id="fa55b-107">The grammar defines the syntax of formal languages.</span></span> <span data-ttu-id="fa55b-108">V následující tabulce jsou uvedeny lexikální pravidla, která popisují, jak rozpoznat platný vstup.</span><span class="sxs-lookup"><span data-stu-id="fa55b-108">The following table lists lexical rules that describe how to recognize a valid input.</span></span> <span data-ttu-id="fa55b-109">Terminály (prvky, které nejsou další redukovatelné) jsou uvedeny v všechna velká písmena.</span><span class="sxs-lookup"><span data-stu-id="fa55b-109">Terminals (those elements that are not further reducible) are shown in all uppercase letters.</span></span> <span data-ttu-id="fa55b-110">Neterminály (prvky, které jsou dále redukovatelné) jsou uvedeny v řetězcích písmeny nebo jednotlivě v uvozovkách, ale jednoduché uvozovky (') není součástí syntaxe samotný.</span><span class="sxs-lookup"><span data-stu-id="fa55b-110">Nonterminals (those elements that are further reducible) are shown in mixed-case or singly quoted strings, but the single quote (') is not a part of the syntax itself.</span></span> <span data-ttu-id="fa55b-111">Znakem svislé čáry (&#124;) označuje pravidla, která mají dílčí pravidla.</span><span class="sxs-lookup"><span data-stu-id="fa55b-111">The pipe character (&#124;) denotes rules that have subrules.</span></span>

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

## <a name="specifying-special-characters"></a><span data-ttu-id="fa55b-112">Zadávání speciálních znaků</span><span class="sxs-lookup"><span data-stu-id="fa55b-112">Specifying special characters</span></span>

<span data-ttu-id="fa55b-113">V názvu typu je IDENTIFIKÁTOR libovolný platný název určuje podle pravidel objektů jazyka.</span><span class="sxs-lookup"><span data-stu-id="fa55b-113">In a type name, IDENTIFIER is any valid name determined by the rules of a language.</span></span>

<span data-ttu-id="fa55b-114">Použít zpětné lomítko (\\) jako řídicí znak pro oddělení následující klíčová slova, když se použije jako součást IDENTIFIKÁTORU.</span><span class="sxs-lookup"><span data-stu-id="fa55b-114">Use the backslash (\\) as an escape character to separate the following tokens when used as part of IDENTIFIER.</span></span>

|<span data-ttu-id="fa55b-115">Podpisový</span><span class="sxs-lookup"><span data-stu-id="fa55b-115">Token</span></span>|<span data-ttu-id="fa55b-116">Význam</span><span class="sxs-lookup"><span data-stu-id="fa55b-116">Meaning</span></span>|
|-----------|-------------|
|<span data-ttu-id="fa55b-117">\\,</span><span class="sxs-lookup"><span data-stu-id="fa55b-117">\\,</span></span>|<span data-ttu-id="fa55b-118">Oddělovač sestavení.</span><span class="sxs-lookup"><span data-stu-id="fa55b-118">Assembly separator.</span></span>|
|\\+|<span data-ttu-id="fa55b-119">Vnořený typ oddělovače.</span><span class="sxs-lookup"><span data-stu-id="fa55b-119">Nested type separator.</span></span>|
|\\&|<span data-ttu-id="fa55b-120">Typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="fa55b-120">Reference type.</span></span>|
|\\*|<span data-ttu-id="fa55b-121">Typ ukazatele.</span><span class="sxs-lookup"><span data-stu-id="fa55b-121">Pointer type.</span></span>|
|<span data-ttu-id="fa55b-122">\\[</span><span class="sxs-lookup"><span data-stu-id="fa55b-122">\\[</span></span>|<span data-ttu-id="fa55b-123">Oddělovač rozměru pole.</span><span class="sxs-lookup"><span data-stu-id="fa55b-123">Array dimension delimiter.</span></span>|
|<span data-ttu-id="fa55b-124">\\]</span><span class="sxs-lookup"><span data-stu-id="fa55b-124">\\]</span></span>|<span data-ttu-id="fa55b-125">Oddělovač rozměru pole.</span><span class="sxs-lookup"><span data-stu-id="fa55b-125">Array dimension delimiter.</span></span>|
|<span data-ttu-id="fa55b-126">\\.</span><span class="sxs-lookup"><span data-stu-id="fa55b-126">\\.</span></span>|<span data-ttu-id="fa55b-127">Použijte zpětné lomítko před tečku pouze v případě, že období se používá ve specifikaci pole.</span><span class="sxs-lookup"><span data-stu-id="fa55b-127">Use the backslash before a period only if the period is used in an array specification.</span></span> <span data-ttu-id="fa55b-128">Období NamespaceSpec nepřebírají zpětné lomítko.</span><span class="sxs-lookup"><span data-stu-id="fa55b-128">Periods in NamespaceSpec do not take the backslash.</span></span>|
|<span data-ttu-id="fa55b-129">\\\|Zpětné lomítko, v případě potřeby jako řetězcový literál.</span><span class="sxs-lookup"><span data-stu-id="fa55b-129">\\\|Backslash when needed as a string literal.</span></span>|

<span data-ttu-id="fa55b-130">Všimněte si, že v všechny součásti token TypeSpec s výjimkou AssemblyNameSpec prostory relevantní.</span><span class="sxs-lookup"><span data-stu-id="fa55b-130">Note that in all TypeSpec components except AssemblyNameSpec, spaces are relevant.</span></span> <span data-ttu-id="fa55b-131">V AssemblyNameSpec souvisí mezery před oddělovačem ',', ale mezery za oddělovačem ',' jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="fa55b-131">In the AssemblyNameSpec, spaces before the ',' separator are relevant, but spaces after the ',' separator are ignored.</span></span>

<span data-ttu-id="fa55b-132">Reflexe třídy, jako například <xref:System.Type.FullName%2A?displayProperty=nameWithType>, vrátí pozměněný název tak, aby vrácený název lze použít ve volání <xref:System.Type.GetType%2A>, například `MyType.GetType(myType.FullName)`.</span><span class="sxs-lookup"><span data-stu-id="fa55b-132">Reflection classes, such as <xref:System.Type.FullName%2A?displayProperty=nameWithType>, return the mangled name so that the returned name can be used in a call to <xref:System.Type.GetType%2A>, as in `MyType.GetType(myType.FullName)`.</span></span>

<span data-ttu-id="fa55b-133">Například plně kvalifikovaný název pro typ může být `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="fa55b-133">For example, the fully qualified name for a type might be `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span></span>

<span data-ttu-id="fa55b-134">Pokud byly oboru názvů `Ozzy.Out+Back`, klepněte na znaménko plus musí být předcházen zpětným lomítkem.</span><span class="sxs-lookup"><span data-stu-id="fa55b-134">If the namespace were `Ozzy.Out+Back`, then the plus sign must be preceded by a backslash.</span></span> <span data-ttu-id="fa55b-135">V opačném případě by analyzátor toto jako oddělovač vnoření.</span><span class="sxs-lookup"><span data-stu-id="fa55b-135">Otherwise, the parser would interpret it as a nesting separator.</span></span> <span data-ttu-id="fa55b-136">Reflexe generuje tento řetězec jako `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="fa55b-136">Reflection emits this string as `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span></span>

## <a name="specifying-assembly-names"></a><span data-ttu-id="fa55b-137">Zadání názvu sestavení</span><span class="sxs-lookup"><span data-stu-id="fa55b-137">Specifying assembly names</span></span>

<span data-ttu-id="fa55b-138">Minimum informací potřebných v specifikaci název sestavení je textový název sestavení (IDENTIFIKÁTOR).</span><span class="sxs-lookup"><span data-stu-id="fa55b-138">The minimum information required in an assembly name specification is the textual name (IDENTIFIER) of the assembly.</span></span> <span data-ttu-id="fa55b-139">Následují tento IDENTIFIKÁTOR čárkou oddělený seznam dvojic vlastnost hodnota, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="fa55b-139">You can follow the IDENTIFIER by a comma-separated list of property/value pairs as described in the following table.</span></span> <span data-ttu-id="fa55b-140">Názvy identifikátorů by měla dodržovat pravidla pro pojmenovávání souborů.</span><span class="sxs-lookup"><span data-stu-id="fa55b-140">IDENTIFIER naming should follow the rules for file naming.</span></span> <span data-ttu-id="fa55b-141">IDENTIFIKÁTOR je velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="fa55b-141">The IDENTIFIER is case-insensitive.</span></span>

|<span data-ttu-id="fa55b-142">Název vlastnosti</span><span class="sxs-lookup"><span data-stu-id="fa55b-142">Property name</span></span>|<span data-ttu-id="fa55b-143">Popis</span><span class="sxs-lookup"><span data-stu-id="fa55b-143">Description</span></span>|<span data-ttu-id="fa55b-144">Povolené hodnoty</span><span class="sxs-lookup"><span data-stu-id="fa55b-144">Allowable values</span></span>|
|-------------------|-----------------|----------------------|
|<span data-ttu-id="fa55b-145">**Verze**</span><span class="sxs-lookup"><span data-stu-id="fa55b-145">**Version**</span></span>|<span data-ttu-id="fa55b-146">Číslo verze sestavení</span><span class="sxs-lookup"><span data-stu-id="fa55b-146">Assembly version number</span></span>|<span data-ttu-id="fa55b-147">*Major.Minor.Build.Revision*, kde *hlavní*, *menší*, *sestavení*, a *revize* jsou celá čísla mezi 0 a 65535 (včetně).</span><span class="sxs-lookup"><span data-stu-id="fa55b-147">*Major.Minor.Build.Revision*, where *Major*, *Minor*, *Build*, and *Revision* are integers between 0 and 65535 inclusive.</span></span>|
|<span data-ttu-id="fa55b-148">**PublicKey**</span><span class="sxs-lookup"><span data-stu-id="fa55b-148">**PublicKey**</span></span>|<span data-ttu-id="fa55b-149">Plně veřejný klíč</span><span class="sxs-lookup"><span data-stu-id="fa55b-149">Full public key</span></span>|<span data-ttu-id="fa55b-150">Hodnota úplného veřejný klíč v šestnáctkovém formátu řetězce.</span><span class="sxs-lookup"><span data-stu-id="fa55b-150">String value of full public key in hexadecimal format.</span></span> <span data-ttu-id="fa55b-151">Zadejte odkaz s hodnotou null (**nic** v jazyce Visual Basic) explicitně určit soukromé sestavení.</span><span class="sxs-lookup"><span data-stu-id="fa55b-151">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="fa55b-152">**PublicKeyToken**</span><span class="sxs-lookup"><span data-stu-id="fa55b-152">**PublicKeyToken**</span></span>|<span data-ttu-id="fa55b-153">Token veřejného klíče (8 bajtů hash veřejného klíče)</span><span class="sxs-lookup"><span data-stu-id="fa55b-153">Public key token (8-byte hash of the full public key)</span></span>|<span data-ttu-id="fa55b-154">Hodnota tokenu veřejného klíče v šestnáctkovém formátu řetězce.</span><span class="sxs-lookup"><span data-stu-id="fa55b-154">String value of public key token in hexadecimal format.</span></span> <span data-ttu-id="fa55b-155">Zadejte odkaz s hodnotou null (**nic** v jazyce Visual Basic) explicitně určit soukromé sestavení.</span><span class="sxs-lookup"><span data-stu-id="fa55b-155">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="fa55b-156">**Jazyková verze**</span><span class="sxs-lookup"><span data-stu-id="fa55b-156">**Culture**</span></span>|<span data-ttu-id="fa55b-157">Jazyková verze sestavení</span><span class="sxs-lookup"><span data-stu-id="fa55b-157">Assembly culture</span></span>|<span data-ttu-id="fa55b-158">Jazyková verze sestavení ve formátu RFC 1766, nebo "neutrální" pro sestavení nezávislým na jazyku (nonsatellite).</span><span class="sxs-lookup"><span data-stu-id="fa55b-158">Culture of the assembly in RFC-1766 format, or "neutral" for language-independent (nonsatellite) assemblies.</span></span>|
|<span data-ttu-id="fa55b-159">**Vlastní**</span><span class="sxs-lookup"><span data-stu-id="fa55b-159">**Custom**</span></span>|<span data-ttu-id="fa55b-160">Vlastní binární velkých objektů (BLOB).</span><span class="sxs-lookup"><span data-stu-id="fa55b-160">Custom binary large object (BLOB).</span></span> <span data-ttu-id="fa55b-161">Tím se aktuálně používá pouze v sestaveních generovaných [Native Image Generator (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="fa55b-161">This is currently used only in assemblies generated by the [Native Image Generator (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>|<span data-ttu-id="fa55b-162">Vlastní řetězec použitý nástrojem Native Image Generator sestavení mezipaměti upozornit, že je nativní bitové kopie sestavení probíhá instalace a proto má být nainstalován v mezipaměti nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="fa55b-162">Custom string used by the Native Image Generator tool to notify the assembly cache that the assembly being installed is a native image, and is therefore to be installed in the native image cache.</span></span> <span data-ttu-id="fa55b-163">Nazývá se také řetězec zap.</span><span class="sxs-lookup"><span data-stu-id="fa55b-163">Also called a zap string.</span></span>|

<span data-ttu-id="fa55b-164">Následující příklad ukazuje **AssemblyName** pro sestavení s jednoduchým názvem s výchozí jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="fa55b-164">The following example shows an **AssemblyName** for a simply named assembly with default culture.</span></span>

```csharp
com.microsoft.crypto, Culture=""
```

<span data-ttu-id="fa55b-165">Následující příklad ukazuje plně zadaný odkaz pro sestavení se silným názvem pomocí jazykové verze "en".</span><span class="sxs-lookup"><span data-stu-id="fa55b-165">The following example shows a fully specified reference for a strongly named assembly with culture "en".</span></span>

```csharp
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

<span data-ttu-id="fa55b-166">Následující příklady ukazují, částečně určeného **AssemblyName**, které je možné splnit silné nebo sestavení s jednoduchým názvem.</span><span class="sxs-lookup"><span data-stu-id="fa55b-166">The following examples each show a partially specified **AssemblyName**, which can be satisfied by either a strong or a simply named assembly.</span></span>

```csharp
com.microsoft.crypto
com.microsoft.crypto, Culture=""
com.microsoft.crypto, Culture=en
```

<span data-ttu-id="fa55b-167">Následující příklady ukazují, částečně určeného **AssemblyName**, které musí být splněno sestavení s jednoduchým názvem.</span><span class="sxs-lookup"><span data-stu-id="fa55b-167">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a simply named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=null
com.microsoft.crypto, Culture=en, PublicKeyToken=null
```

<span data-ttu-id="fa55b-168">Následující příklady ukazují, částečně určeného **AssemblyName**, které musí být splněno sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="fa55b-168">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a strongly named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

## <a name="specifying-generic-types"></a><span data-ttu-id="fa55b-169">Zadání obecných typů</span><span class="sxs-lookup"><span data-stu-id="fa55b-169">Specifying generic types</span></span>

<span data-ttu-id="fa55b-170">SimpleTypeSpec\`číslo představuje otevřený obecný typ. se od 1 do *n* parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="fa55b-170">SimpleTypeSpec\`NUMBER represents an open generic type with from 1 to *n* generic type parameters.</span></span> <span data-ttu-id="fa55b-171">Například chcete získat odkaz na otevřený obecný typ. seznamu\<T > nebo uzavřený obecný typ seznamu\<řetězec >, použijte ``Type.GetType("System.Collections.Generic.List`1")`` získáte odkaz na obecný typ slovníku\<TKey, TValue >, použijte ``Type.GetType("System.Collections.Generic.Dictionary`2")``.</span><span class="sxs-lookup"><span data-stu-id="fa55b-171">For example, to get reference to the open generic type List\<T> or the closed generic type List\<String>, use ``Type.GetType("System.Collections.Generic.List`1")`` To get a reference to the generic type Dictionary\<TKey,TValue>, use ``Type.GetType("System.Collections.Generic.Dictionary`2")``.</span></span>

## <a name="specifying-pointers"></a><span data-ttu-id="fa55b-172">Určení ukazatele</span><span class="sxs-lookup"><span data-stu-id="fa55b-172">Specifying pointers</span></span>

<span data-ttu-id="fa55b-173">SimpleTypeSpec \* představuje nespravovaný ukazatel.</span><span class="sxs-lookup"><span data-stu-id="fa55b-173">SimpleTypeSpec\* represents an unmanaged pointer.</span></span> <span data-ttu-id="fa55b-174">Například ukazatele na typ MyType získáte pomocí `Type.GetType("MyType*")`.</span><span class="sxs-lookup"><span data-stu-id="fa55b-174">For example, to get a pointer to type MyType, use `Type.GetType("MyType*")`.</span></span> <span data-ttu-id="fa55b-175">Chcete-li získat ukazatel na ukazatel na typ MyType, použijte `Type.GetType("MyType**")`.</span><span class="sxs-lookup"><span data-stu-id="fa55b-175">To get a pointer to a pointer to type MyType, use `Type.GetType("MyType**")`.</span></span>

## <a name="specifying-references"></a><span data-ttu-id="fa55b-176">Určení odkazy</span><span class="sxs-lookup"><span data-stu-id="fa55b-176">Specifying references</span></span>

<span data-ttu-id="fa55b-177">SimpleTypeSpec & představuje spravovaného ukazatele nebo odkazu.</span><span class="sxs-lookup"><span data-stu-id="fa55b-177">SimpleTypeSpec & represents a managed pointer or reference.</span></span> <span data-ttu-id="fa55b-178">Například pokud chcete získat odkaz na typ MyType, použít `Type.GetType("MyType &")`.</span><span class="sxs-lookup"><span data-stu-id="fa55b-178">For example, to get a reference to type MyType, use `Type.GetType("MyType &")`.</span></span> <span data-ttu-id="fa55b-179">Všimněte si, že na rozdíl od ukazatelů, odkazů jsou omezené na jedné úrovni.</span><span class="sxs-lookup"><span data-stu-id="fa55b-179">Note that unlike pointers, references are limited to one level.</span></span>

## <a name="specifying-arrays"></a><span data-ttu-id="fa55b-180">Určení polí</span><span class="sxs-lookup"><span data-stu-id="fa55b-180">Specifying arrays</span></span>

<span data-ttu-id="fa55b-181">V BNF – gramatika ReflectionEmitDimension platí jenom pro definice nekompletní typ načten pomocí možnosti <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fa55b-181">In the BNF Grammar, ReflectionEmitDimension only applies to incomplete type definitions retrieved using <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fa55b-182">Definice neúplného typu jsou <xref:System.Reflection.Emit.TypeBuilder> objekty, které jsou vytvářeny pomocí <xref:System.Reflection.Emit?displayProperty=nameWithType> ale na které <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> se nevolala.</span><span class="sxs-lookup"><span data-stu-id="fa55b-182">Incomplete type definitions are <xref:System.Reflection.Emit.TypeBuilder> objects constructed using <xref:System.Reflection.Emit?displayProperty=nameWithType> but on which <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> has not been called.</span></span> <span data-ttu-id="fa55b-183">ReflectionDimension slouží k načtení žádné definice typu, která byla dokončena, to znamená typ, který se načetl.</span><span class="sxs-lookup"><span data-stu-id="fa55b-183">ReflectionDimension can be used to retrieve any type definition that has been completed, that is, a type that has been loaded.</span></span>

<span data-ttu-id="fa55b-184">Pole jsou přístupné v reflexi tak, že určíte počet rozměrů pole:</span><span class="sxs-lookup"><span data-stu-id="fa55b-184">Arrays are accessed in reflection by specifying the rank of the array:</span></span>

- <span data-ttu-id="fa55b-185">`Type.GetType("MyArray[]")` Získá pole s jednou dimenzí s dolní mez 0.</span><span class="sxs-lookup"><span data-stu-id="fa55b-185">`Type.GetType("MyArray[]")` gets a single-dimension array with 0 lower bound.</span></span>

- <span data-ttu-id="fa55b-186">`Type.GetType("MyArray[*]")` Získá pole s jednou dimenzí s neznámým rozsahem. nižší.</span><span class="sxs-lookup"><span data-stu-id="fa55b-186">`Type.GetType("MyArray[*]")` gets a single-dimension array with unknown lower bound.</span></span>
- <span data-ttu-id="fa55b-187">`Type.GetType("MyArray[][]")` Získá pole dvourozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="fa55b-187">`Type.GetType("MyArray[][]")` gets a two-dimensional array's array.</span></span>

- <span data-ttu-id="fa55b-188">`Type.GetType("MyArray[*,*]")` a `Type.GetType("MyArray[,]")` získá obdélníkové dvojrozměrné pole s Neznámý dolní meze.</span><span class="sxs-lookup"><span data-stu-id="fa55b-188">`Type.GetType("MyArray[*,*]")` and `Type.GetType("MyArray[,]")` gets a rectangular two-dimensional array with unknown lower bounds.</span></span>

<span data-ttu-id="fa55b-189">Všimněte si, že z modulu runtime pohledu `MyArray[] != MyArray[*]`, ale pro vícerozměrná pole jsou ekvivalentní zápisy dva.</span><span class="sxs-lookup"><span data-stu-id="fa55b-189">Note that from a runtime point of view, `MyArray[] != MyArray[*]`, but for multidimensional arrays, the two notations are equivalent.</span></span> <span data-ttu-id="fa55b-190">To znamená `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` vyhodnotí jako **true**.</span><span class="sxs-lookup"><span data-stu-id="fa55b-190">That is, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` evaluates to **true**.</span></span>

<span data-ttu-id="fa55b-191">Pro **ModuleBuilder.GetType**, `MyArray[0..5]` určuje pole s jednou dimenzí s velikostí 6, dolní meze 0.</span><span class="sxs-lookup"><span data-stu-id="fa55b-191">For **ModuleBuilder.GetType**, `MyArray[0..5]` indicates a single-dimension array with size 6, lower bound 0.</span></span> <span data-ttu-id="fa55b-192">`MyArray[4…]` označuje jednou dimenzí pole neznámé velikosti a dolní mez 4.</span><span class="sxs-lookup"><span data-stu-id="fa55b-192">`MyArray[4…]` indicates a single-dimension array of unknown size and lower bound 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa55b-193">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa55b-193">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- <xref:System.Reflection.Emit.ModuleBuilder>
- <xref:System.Reflection.Emit.TypeBuilder>
- <xref:System.Type.FullName%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>
- [<span data-ttu-id="fa55b-194">Zobrazení informací o typu</span><span class="sxs-lookup"><span data-stu-id="fa55b-194">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
