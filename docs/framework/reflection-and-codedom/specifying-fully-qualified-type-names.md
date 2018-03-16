---
title: "Určení úplných názvů typů"
ms.custom: 
ms.date: 03/14/2018
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e31e6e0284de44768b2faad7bcf84d5be343e479
ms.sourcegitcommit: 1c0b0f082b3f300e54b4d069b317ac724c88ddc3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2018
---
# <a name="specifying-fully-qualified-type-names"></a><span data-ttu-id="38ca9-102">Určení úplných názvů typů</span><span class="sxs-lookup"><span data-stu-id="38ca9-102">Specifying Fully Qualified Type Names</span></span>
<span data-ttu-id="38ca9-103">Je nutné zadat názvy typů tak, aby měl platný vstup pro různé operace reflexe.</span><span class="sxs-lookup"><span data-stu-id="38ca9-103">You must specify type names to have valid input to various reflection operations.</span></span> <span data-ttu-id="38ca9-104">Název plně kvalifikovaný typ se skládá z specifikace název sestavení, oboru názvů a název typu.</span><span class="sxs-lookup"><span data-stu-id="38ca9-104">A fully qualified type name consists of an assembly name specification, a namespace specification, and a type name.</span></span> <span data-ttu-id="38ca9-105">Zadejte název specifikace jsou používány metody, jako <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, a <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="38ca9-105">Type name specifications are used by methods such as <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, and <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="grammar-for-type-names"></a><span data-ttu-id="38ca9-106">Gramatika pro názvy typů</span><span class="sxs-lookup"><span data-stu-id="38ca9-106">Grammar for Type Names</span></span>  
 <span data-ttu-id="38ca9-107">Gramatiky definuje syntaxe formální jazyky.</span><span class="sxs-lookup"><span data-stu-id="38ca9-107">The grammar defines the syntax of formal languages.</span></span> <span data-ttu-id="38ca9-108">Následující tabulka uvádí lexikální pravidla, které popisují, jak rozpoznat platné zadání.</span><span class="sxs-lookup"><span data-stu-id="38ca9-108">The following table lists lexical rules that describe how to recognize a valid input.</span></span> <span data-ttu-id="38ca9-109">Terminály (elementy, které nejsou další reducible) se zobrazí velkými písmeny.</span><span class="sxs-lookup"><span data-stu-id="38ca9-109">Terminals (those elements that are not further reducible) are shown in all uppercase letters.</span></span> <span data-ttu-id="38ca9-110">Terminálově nezávislých (elementy, které jsou dále reducible) jsou uvedeny v řetězcích rozlišením malých a samostatně uvozovkách, ale jednoduché uvozovky (') není součástí syntaxe sám sebe.</span><span class="sxs-lookup"><span data-stu-id="38ca9-110">Nonterminals (those elements that are further reducible) are shown in mixed-case or singly quoted strings, but the single quote (') is not a part of the syntax itself.</span></span> <span data-ttu-id="38ca9-111">Svislou čarou (&#124;) označuje pravidla, která mají dílčích pravidel.</span><span class="sxs-lookup"><span data-stu-id="38ca9-111">The pipe character (&#124;) denotes rules that have subrules.</span></span>  

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
    | ArrayTypeSpec
    | TypeName
    ;

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

## <a name="specifying-special-characters"></a><span data-ttu-id="38ca9-112">Zadání speciální znaky</span><span class="sxs-lookup"><span data-stu-id="38ca9-112">Specifying Special Characters</span></span>  
 <span data-ttu-id="38ca9-113">Název typu je IDENTIFIKÁTOR libovolný platný název určit pravidly jazyka.</span><span class="sxs-lookup"><span data-stu-id="38ca9-113">In a type name, IDENTIFIER is any valid name determined by the rules of a language.</span></span>  
  
 <span data-ttu-id="38ca9-114">Použít zpětné lomítko (\\) jako řídicí znak oddělit následující klíčová slova, pokud se používá jako součást IDENTIFIKÁTORU.</span><span class="sxs-lookup"><span data-stu-id="38ca9-114">Use the backslash (\\) as an escape character to separate the following tokens when used as part of IDENTIFIER.</span></span>  
  
|<span data-ttu-id="38ca9-115">Token</span><span class="sxs-lookup"><span data-stu-id="38ca9-115">Token</span></span>|<span data-ttu-id="38ca9-116">Význam</span><span class="sxs-lookup"><span data-stu-id="38ca9-116">Meaning</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="38ca9-117">\\,</span><span class="sxs-lookup"><span data-stu-id="38ca9-117">\\,</span></span>|<span data-ttu-id="38ca9-118">Oddělovač sestavení.</span><span class="sxs-lookup"><span data-stu-id="38ca9-118">Assembly separator.</span></span>|  
|\\+|<span data-ttu-id="38ca9-119">Vnořené typy oddělovače.</span><span class="sxs-lookup"><span data-stu-id="38ca9-119">Nested type separator.</span></span>|  
|\\&|<span data-ttu-id="38ca9-120">Typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="38ca9-120">Reference type.</span></span>|  
|\\*|<span data-ttu-id="38ca9-121">Typ ukazatele.</span><span class="sxs-lookup"><span data-stu-id="38ca9-121">Pointer type.</span></span>|  
|<span data-ttu-id="38ca9-122">\\[</span><span class="sxs-lookup"><span data-stu-id="38ca9-122">\\[</span></span>|<span data-ttu-id="38ca9-123">Pole dimenze oddělovač.</span><span class="sxs-lookup"><span data-stu-id="38ca9-123">Array dimension delimiter.</span></span>|  
|<span data-ttu-id="38ca9-124">\\]</span><span class="sxs-lookup"><span data-stu-id="38ca9-124">\\]</span></span>|<span data-ttu-id="38ca9-125">Pole dimenze oddělovač.</span><span class="sxs-lookup"><span data-stu-id="38ca9-125">Array dimension delimiter.</span></span>|  
|<span data-ttu-id="38ca9-126">\\.</span><span class="sxs-lookup"><span data-stu-id="38ca9-126">\\.</span></span>|<span data-ttu-id="38ca9-127">Použijte zpětné lomítko před dobou pouze v případě, že období se používá v specifikace pole.</span><span class="sxs-lookup"><span data-stu-id="38ca9-127">Use the backslash before a period only if the period is used in an array specification.</span></span> <span data-ttu-id="38ca9-128">Tečky v NamespaceSpec nepřebírají zpětné lomítko.</span><span class="sxs-lookup"><span data-stu-id="38ca9-128">Periods in NamespaceSpec do not take the backslash.</span></span>|  
|<span data-ttu-id="38ca9-129">\\\|Zpětné lomítko, v případě potřeby jako řetězcový literál.</span><span class="sxs-lookup"><span data-stu-id="38ca9-129">\\\|Backslash when needed as a string literal.</span></span>|  
  
 <span data-ttu-id="38ca9-130">Upozorňujeme, že v všechny součásti typ TypeSpec s výjimkou AssemblyNameSpec, jsou relevantní prostory.</span><span class="sxs-lookup"><span data-stu-id="38ca9-130">Note that in all TypeSpec components except AssemblyNameSpec, spaces are relevant.</span></span> <span data-ttu-id="38ca9-131">V AssemblyNameSpec jsou relevantní prostory před oddělovač ',', ale mezery po ',' oddělovač jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="38ca9-131">In the AssemblyNameSpec, spaces before the ',' separator are relevant, but spaces after the ',' separator are ignored.</span></span>  
  
 <span data-ttu-id="38ca9-132">Reflexe třídy, jako například <xref:System.Type.FullName%2A?displayProperty=nameWithType>, vrátí pozměnění název tak, aby vrácený název lze použít v volání <xref:System.Type.GetType%2A>jako v `MyType.GetType(myType.FullName)`.</span><span class="sxs-lookup"><span data-stu-id="38ca9-132">Reflection classes, such as <xref:System.Type.FullName%2A?displayProperty=nameWithType>, return the mangled name so that the returned name can be used in a call to <xref:System.Type.GetType%2A>, as in `MyType.GetType(myType.FullName)`.</span></span>  
  
 <span data-ttu-id="38ca9-133">Například může být plně kvalifikovaný název typu `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="38ca9-133">For example, the fully qualified name for a type might be `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span></span>  
  
 <span data-ttu-id="38ca9-134">Pokud byly oboru názvů `Ozzy.Out+Back`, pak na symbol plus musí předcházet zpětné lomítko.</span><span class="sxs-lookup"><span data-stu-id="38ca9-134">If the namespace were `Ozzy.Out+Back`, then the plus sign must be preceded by a backslash.</span></span> <span data-ttu-id="38ca9-135">Jinak by analyzátor toto jako oddělovač vnoření.</span><span class="sxs-lookup"><span data-stu-id="38ca9-135">Otherwise, the parser would interpret it as a nesting separator.</span></span> <span data-ttu-id="38ca9-136">Reflexe vysílá tento řetězec jako `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="38ca9-136">Reflection emits this string as `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span></span>  
  
## <a name="specifying-assembly-names"></a><span data-ttu-id="38ca9-137">Určení názvy sestavení</span><span class="sxs-lookup"><span data-stu-id="38ca9-137">Specifying Assembly Names</span></span>  
 <span data-ttu-id="38ca9-138">Minimální informace požadované specifikací název sestavení je textový název sestavení (IDENTIFIER).</span><span class="sxs-lookup"><span data-stu-id="38ca9-138">The minimum information required in an assembly name specification is the textual name (IDENTIFIER) of the assembly.</span></span> <span data-ttu-id="38ca9-139">IDENTIFIKÁTOR můžete provést pomocí seznam oddělený čárkami dvojic vlastnost/hodnota, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="38ca9-139">You can follow the IDENTIFIER by a comma-separated list of property/value pairs as described in the following table.</span></span> <span data-ttu-id="38ca9-140">IDENTIFIKÁTOR pojmenování by mělo vycházet pravidla pro pojmenovávání souborů.</span><span class="sxs-lookup"><span data-stu-id="38ca9-140">IDENTIFIER naming should follow the rules for file naming.</span></span> <span data-ttu-id="38ca9-141">IDENTIFIKÁTOR nerozlišuje velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="38ca9-141">The IDENTIFIER is case-insensitive.</span></span>  
  
|<span data-ttu-id="38ca9-142">Název vlastnosti</span><span class="sxs-lookup"><span data-stu-id="38ca9-142">Property name</span></span>|<span data-ttu-id="38ca9-143">Popis</span><span class="sxs-lookup"><span data-stu-id="38ca9-143">Description</span></span>|<span data-ttu-id="38ca9-144">Povolené hodnoty</span><span class="sxs-lookup"><span data-stu-id="38ca9-144">Allowable values</span></span>|  
|-------------------|-----------------|----------------------|  
|<span data-ttu-id="38ca9-145">**Verze**</span><span class="sxs-lookup"><span data-stu-id="38ca9-145">**Version**</span></span>|<span data-ttu-id="38ca9-146">Číslo verze sestavení</span><span class="sxs-lookup"><span data-stu-id="38ca9-146">Assembly version number</span></span>|<span data-ttu-id="38ca9-147">*Major.Minor.Build.Revision*, kde *hlavní*, *menší*, *sestavení*, a *revize* jsou celá čísla mezi 0 a 65535 (včetně).</span><span class="sxs-lookup"><span data-stu-id="38ca9-147">*Major.Minor.Build.Revision*, where *Major*, *Minor*, *Build*, and *Revision* are integers between 0 and 65535 inclusive.</span></span>|  
|<span data-ttu-id="38ca9-148">**PublicKey**</span><span class="sxs-lookup"><span data-stu-id="38ca9-148">**PublicKey**</span></span>|<span data-ttu-id="38ca9-149">Úplné veřejný klíč</span><span class="sxs-lookup"><span data-stu-id="38ca9-149">Full public key</span></span>|<span data-ttu-id="38ca9-150">Řetězec hodnotu úplné veřejný klíč v šestnáctkovém formátu.</span><span class="sxs-lookup"><span data-stu-id="38ca9-150">String value of full public key in hexadecimal format.</span></span> <span data-ttu-id="38ca9-151">Zadejte odkaz s hodnotou null (**nic** v jazyce Visual Basic) explicitně udávajících privátní sestavení.</span><span class="sxs-lookup"><span data-stu-id="38ca9-151">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|  
|<span data-ttu-id="38ca9-152">**PublicKeyToken**</span><span class="sxs-lookup"><span data-stu-id="38ca9-152">**PublicKeyToken**</span></span>|<span data-ttu-id="38ca9-153">Token veřejného klíče (8 bajtů hash veřejného klíče)</span><span class="sxs-lookup"><span data-stu-id="38ca9-153">Public key token (8-byte hash of the full public key)</span></span>|<span data-ttu-id="38ca9-154">Hodnota tokenu veřejného klíče v šestnáctkovém formátu řetězec.</span><span class="sxs-lookup"><span data-stu-id="38ca9-154">String value of public key token in hexadecimal format.</span></span> <span data-ttu-id="38ca9-155">Zadejte odkaz s hodnotou null (**nic** v jazyce Visual Basic) explicitně udávajících privátní sestavení.</span><span class="sxs-lookup"><span data-stu-id="38ca9-155">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|  
|<span data-ttu-id="38ca9-156">**Jazyková verze**</span><span class="sxs-lookup"><span data-stu-id="38ca9-156">**Culture**</span></span>|<span data-ttu-id="38ca9-157">Jazyková verze sestavení</span><span class="sxs-lookup"><span data-stu-id="38ca9-157">Assembly culture</span></span>|<span data-ttu-id="38ca9-158">Jazyková verze sestavení ve formátu RFC 1766, nebo "neutrální" pro sestavení nezávislé na jazyku (nonsatellite).</span><span class="sxs-lookup"><span data-stu-id="38ca9-158">Culture of the assembly in RFC-1766 format, or "neutral" for language-independent (nonsatellite) assemblies.</span></span>|  
|<span data-ttu-id="38ca9-159">**Vlastní**</span><span class="sxs-lookup"><span data-stu-id="38ca9-159">**Custom**</span></span>|<span data-ttu-id="38ca9-160">Vlastní binární rozsáhlý objekt (binární rozsáhlý OBJEKT).</span><span class="sxs-lookup"><span data-stu-id="38ca9-160">Custom binary large object (BLOB).</span></span> <span data-ttu-id="38ca9-161">To se aktuálně používá jenom v sestavení, které jsou generované [generátor (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="38ca9-161">This is currently used only in assemblies generated by the [Native Image Generator (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>|<span data-ttu-id="38ca9-162">Vlastní řetězec nástroje Generátor pro mezipaměť sestavení upozornit, že je nativních bitových kopií sestavení instaluje a proto má být nainstalován v mezipaměť nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="38ca9-162">Custom string used by the Native Image Generator tool to notify the assembly cache that the assembly being installed is a native image, and is therefore to be installed in the native image cache.</span></span> <span data-ttu-id="38ca9-163">Také nazývá zap řetězec.</span><span class="sxs-lookup"><span data-stu-id="38ca9-163">Also called a zap string.</span></span>|  
  
 <span data-ttu-id="38ca9-164">Následující příklad ukazuje **AssemblyName** pro jednoduše pojmenované sestavení s výchozí jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="38ca9-164">The following example shows an **AssemblyName** for a simply named assembly with default culture.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture=""   
```  
  
 <span data-ttu-id="38ca9-165">Následující příklad ukazuje plně zadaný odkaz pro silně pojmenované sestavení s jazykovou verzi "en".</span><span class="sxs-lookup"><span data-stu-id="38ca9-165">The following example shows a fully specified reference for a strongly named assembly with culture "en".</span></span>  
  
```csharp  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0   
```  
  
 <span data-ttu-id="38ca9-166">Následující příklady ukazují, částečně zadané **AssemblyName**, který může obsloužit silné nebo jednoduše pojmenované sestavení.</span><span class="sxs-lookup"><span data-stu-id="38ca9-166">The following examples each show a partially specified **AssemblyName**, which can be satisfied by either a strong or a simply named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto  
com.microsoft.crypto, Culture=""  
com.microsoft.crypto, Culture=en   
```  
  
 <span data-ttu-id="38ca9-167">Následující příklady ukazují, částečně zadané **AssemblyName**, které musí splnit jednoduše pojmenované sestavení.</span><span class="sxs-lookup"><span data-stu-id="38ca9-167">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a simply named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=null   
com.microsoft.crypto, Culture=en, PublicKeyToken=null  
```  
  
 <span data-ttu-id="38ca9-168">Následující příklady ukazují, částečně zadané **AssemblyName**, které musí splnit silně pojmenované sestavení.</span><span class="sxs-lookup"><span data-stu-id="38ca9-168">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a strongly named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0  
```  
  
## <a name="specifying-pointers"></a><span data-ttu-id="38ca9-169">Určení ukazatele</span><span class="sxs-lookup"><span data-stu-id="38ca9-169">Specifying Pointers</span></span>  
 <span data-ttu-id="38ca9-170">SimpleTypeSpec \* představuje nespravovaný ukazatel.</span><span class="sxs-lookup"><span data-stu-id="38ca9-170">SimpleTypeSpec\* represents an unmanaged pointer.</span></span> <span data-ttu-id="38ca9-171">Například ukazatel na typ MyType získáte pomocí `Type.GetType("MyType*")`.</span><span class="sxs-lookup"><span data-stu-id="38ca9-171">For example, to get a pointer to type MyType, use `Type.GetType("MyType*")`.</span></span> <span data-ttu-id="38ca9-172">Ukazatel na ukazatel na typ MyType získáte pomocí `Type.GetType("MyType**")`.</span><span class="sxs-lookup"><span data-stu-id="38ca9-172">To get a pointer to a pointer to type MyType, use `Type.GetType("MyType**")`.</span></span>  
  
## <a name="specifying-references"></a><span data-ttu-id="38ca9-173">Určení odkazy</span><span class="sxs-lookup"><span data-stu-id="38ca9-173">Specifying References</span></span>  
 <span data-ttu-id="38ca9-174">SimpleTypeSpec & reprezentuje spravované ukazatel nebo odkaz.</span><span class="sxs-lookup"><span data-stu-id="38ca9-174">SimpleTypeSpec & represents a managed pointer or reference.</span></span> <span data-ttu-id="38ca9-175">Například pokud chcete získat odkaz na typ MyType, použijte `Type.GetType("MyType &")`.</span><span class="sxs-lookup"><span data-stu-id="38ca9-175">For example, to get a reference to type MyType, use `Type.GetType("MyType &")`.</span></span> <span data-ttu-id="38ca9-176">Všimněte si, že na rozdíl od ukazatele, odkazy jsou omezeny na jedné úrovni.</span><span class="sxs-lookup"><span data-stu-id="38ca9-176">Note that unlike pointers, references are limited to one level.</span></span>  
  
## <a name="specifying-arrays"></a><span data-ttu-id="38ca9-177">Určení pole</span><span class="sxs-lookup"><span data-stu-id="38ca9-177">Specifying Arrays</span></span>  
 <span data-ttu-id="38ca9-178">V BNF – gramatika, ReflectionEmitDimension platí pouze pro neúplné typ definice načten pomocí <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="38ca9-178">In the BNF Grammar, ReflectionEmitDimension only applies to incomplete type definitions retrieved using <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="38ca9-179">Jsou neúplné typ definice <xref:System.Reflection.Emit.TypeBuilder> objekty, které jsou vytvářeny pomocí <xref:System.Reflection.Emit?displayProperty=nameWithType> , ale na kterém <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> nebyla volána.</span><span class="sxs-lookup"><span data-stu-id="38ca9-179">Incomplete type definitions are <xref:System.Reflection.Emit.TypeBuilder> objects constructed using <xref:System.Reflection.Emit?displayProperty=nameWithType> but on which <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> has not been called.</span></span> <span data-ttu-id="38ca9-180">ReflectionDimension umožňuje načíst všechny definice typu, která byla dokončena, který je typ, který byl načten.</span><span class="sxs-lookup"><span data-stu-id="38ca9-180">ReflectionDimension can be used to retrieve any type definition that has been completed, that is, a type that has been loaded.</span></span>  
  
 <span data-ttu-id="38ca9-181">Pole jsou přístupné v reflexe určení pořadí pole:</span><span class="sxs-lookup"><span data-stu-id="38ca9-181">Arrays are accessed in reflection by specifying the rank of the array:</span></span>  
  
-   <span data-ttu-id="38ca9-182">`Type.GetType("MyArray[]")` Získá pole jedním dimenze s 0 dolní mez.</span><span class="sxs-lookup"><span data-stu-id="38ca9-182">`Type.GetType("MyArray[]")` gets a single-dimension array with 0 lower bound.</span></span>  
  
-   <span data-ttu-id="38ca9-183">`Type.GetType("MyArray[*]")` Získá pole jedním dimenze s neznámou dolní mez.</span><span class="sxs-lookup"><span data-stu-id="38ca9-183">`Type.GetType("MyArray[*]")` gets a single-dimension array with unknown lower bound.</span></span>  
  
-   <span data-ttu-id="38ca9-184">`Type.GetType("MyArray[][]")` Získá pole dvourozměrná pole.</span><span class="sxs-lookup"><span data-stu-id="38ca9-184">`Type.GetType("MyArray[][]")` gets a two-dimensional array's array.</span></span>  
  
-   <span data-ttu-id="38ca9-185">`Type.GetType("MyArray[*,*]")` a `Type.GetType("MyArray[,]")` získá obdélníková dvourozměrná pole s neznámou dolní meze.</span><span class="sxs-lookup"><span data-stu-id="38ca9-185">`Type.GetType("MyArray[*,*]")` and `Type.GetType("MyArray[,]")` gets a rectangular two-dimensional array with unknown lower bounds.</span></span>  
  
 <span data-ttu-id="38ca9-186">Všimněte si, že se z modulu runtime hlediska, `MyArray[] != MyArray[*]`, ale pro vícerozměrná pole jsou ekvivalentní zápisy dva.</span><span class="sxs-lookup"><span data-stu-id="38ca9-186">Note that from a runtime point of view, `MyArray[] != MyArray[*]`, but for multidimensional arrays, the two notations are equivalent.</span></span> <span data-ttu-id="38ca9-187">To znamená `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` vyhodnotí jako **true**.</span><span class="sxs-lookup"><span data-stu-id="38ca9-187">That is, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` evaluates to **true**.</span></span>  
  
 <span data-ttu-id="38ca9-188">Pro **ModuleBuilder.GetType**, `MyArray[0..5]` označuje jeden dimenze pole s velikostí 6, nižší vázán 0.</span><span class="sxs-lookup"><span data-stu-id="38ca9-188">For **ModuleBuilder.GetType**, `MyArray[0..5]` indicates a single-dimension array with size 6, lower bound 0.</span></span> <span data-ttu-id="38ca9-189">`MyArray[4…]` Určuje pole dimenze jeden neznámý velikost a dolní hranice 4.</span><span class="sxs-lookup"><span data-stu-id="38ca9-189">`MyArray[4…]` indicates a single-dimension array of unknown size and lower bound 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38ca9-190">Viz také</span><span class="sxs-lookup"><span data-stu-id="38ca9-190">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 <xref:System.Reflection.Emit.ModuleBuilder>  
 <xref:System.Reflection.Emit.TypeBuilder>  
 <xref:System.Type.FullName%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="38ca9-191">Zobrazení informací o typu</span><span class="sxs-lookup"><span data-stu-id="38ca9-191">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
