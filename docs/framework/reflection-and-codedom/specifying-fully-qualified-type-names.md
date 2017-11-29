---
title: "Určení úplných názvů typů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- reflection, fully qualified type names
- names [.NET Framework], assemblies
- tokens
- BNF
- assemblies [.NET Framework], names
- Backus-Naur form
- languages, BNF grammar
- fully qualified type names
- type names
- special characters
- IDENTIFIER
ms.assetid: d90b1e39-9115-4f2a-81c0-05e7e74e5580
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6759e7b62f4083f6d53663385398baf098f2676f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="specifying-fully-qualified-type-names"></a><span data-ttu-id="51b1d-102">Určení úplných názvů typů</span><span class="sxs-lookup"><span data-stu-id="51b1d-102">Specifying Fully Qualified Type Names</span></span>
<span data-ttu-id="51b1d-103">Je nutné zadat názvy typů tak, aby měl platný vstup pro různé operace reflexe.</span><span class="sxs-lookup"><span data-stu-id="51b1d-103">You must specify type names to have valid input to various reflection operations.</span></span> <span data-ttu-id="51b1d-104">Název plně kvalifikovaný typ se skládá z specifikace název sestavení, oboru názvů a název typu.</span><span class="sxs-lookup"><span data-stu-id="51b1d-104">A fully qualified type name consists of an assembly name specification, a namespace specification, and a type name.</span></span> <span data-ttu-id="51b1d-105">Zadejte název specifikace jsou používány metody, jako <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, a <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="51b1d-105">Type name specifications are used by methods such as <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, and <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="backus-naur-form-grammar-for-type-names"></a><span data-ttu-id="51b1d-106">Backus-Naur – gramatika formuláře pro názvy typů</span><span class="sxs-lookup"><span data-stu-id="51b1d-106">Backus-Naur Form Grammar for Type Names</span></span>  
 <span data-ttu-id="51b1d-107">Backus-Naur formuláře (BNF) definuje syntaxe formální jazyky.</span><span class="sxs-lookup"><span data-stu-id="51b1d-107">The Backus-Naur form (BNF) defines the syntax of formal languages.</span></span> <span data-ttu-id="51b1d-108">Následující tabulka uvádí BNF lexikální pravidla, které popisují, jak rozpoznat platné zadání.</span><span class="sxs-lookup"><span data-stu-id="51b1d-108">The following table lists BNF lexical rules that describe how to recognize a valid input.</span></span> <span data-ttu-id="51b1d-109">Terminály (elementy, které nejsou další reducible) se zobrazí velkými písmeny.</span><span class="sxs-lookup"><span data-stu-id="51b1d-109">Terminals (those elements that are not further reducible) are shown in all uppercase letters.</span></span> <span data-ttu-id="51b1d-110">Terminálově nezávislých (elementy, které jsou dále reducible) jsou uvedeny v řetězcích rozlišením malých a samostatně uvozovkách, ale jednoduché uvozovky (') není součástí syntaxe sám sebe.</span><span class="sxs-lookup"><span data-stu-id="51b1d-110">Nonterminals (those elements that are further reducible) are shown in mixed-case or singly quoted strings, but the single quote (') is not a part of the syntax itself.</span></span> <span data-ttu-id="51b1d-111">Svislou čarou (&#124;) označuje pravidla, která mají dílčích pravidel.</span><span class="sxs-lookup"><span data-stu-id="51b1d-111">The pipe character (&#124;) denotes rules that have subrules.</span></span>  
  
|<span data-ttu-id="51b1d-112">BNF – gramatika z úplné názvy typů</span><span class="sxs-lookup"><span data-stu-id="51b1d-112">BNF grammar of fully qualified type names</span></span>|  
|-----------------------------------------------|  
|<span data-ttu-id="51b1d-113">Typ TypeSpec: = ReferenceTypeSpec</span><span class="sxs-lookup"><span data-stu-id="51b1d-113">TypeSpec                          :=   ReferenceTypeSpec</span></span><br /><br /> <span data-ttu-id="51b1d-114">&#124;     SimpleTypeSpec</span><span class="sxs-lookup"><span data-stu-id="51b1d-114">&#124;     SimpleTypeSpec</span></span>|  
|<span data-ttu-id="51b1d-115">ReferenceTypeSpec: = SimpleTypeSpec 'a'</span><span class="sxs-lookup"><span data-stu-id="51b1d-115">ReferenceTypeSpec            :=   SimpleTypeSpec '&'</span></span>|  
|<span data-ttu-id="51b1d-116">SimpleTypeSpec: = PointerTypeSpec</span><span class="sxs-lookup"><span data-stu-id="51b1d-116">SimpleTypeSpec                :=   PointerTypeSpec</span></span><br /><br /> <span data-ttu-id="51b1d-117">&#124;     ArrayTypeSpec</span><span class="sxs-lookup"><span data-stu-id="51b1d-117">&#124;     ArrayTypeSpec</span></span><br /><br /> <span data-ttu-id="51b1d-118">&#124;     TypeName</span><span class="sxs-lookup"><span data-stu-id="51b1d-118">&#124;     TypeName</span></span>|  
|<span data-ttu-id="51b1d-119">PointerTypeSpec: = SimpleTypeSpec ' *'</span><span class="sxs-lookup"><span data-stu-id="51b1d-119">PointerTypeSpec                :=   SimpleTypeSpec '*'</span></span>|  
|<span data-ttu-id="51b1d-120">ArrayTypeSpec: = SimpleTypeSpec [ReflectionDimension]</span><span class="sxs-lookup"><span data-stu-id="51b1d-120">ArrayTypeSpec                  :=   SimpleTypeSpec '[ReflectionDimension]'</span></span><br /><br /> <span data-ttu-id="51b1d-121">&#124;     SimpleTypeSpec [ReflectionEmitDimension]</span><span class="sxs-lookup"><span data-stu-id="51b1d-121">&#124;     SimpleTypeSpec '[ReflectionEmitDimension]'</span></span>|  
|<span data-ttu-id="51b1d-122">ReflectionDimension: = ' *'</span><span class="sxs-lookup"><span data-stu-id="51b1d-122">ReflectionDimension           :=   '*'</span></span><br /><br /> <span data-ttu-id="51b1d-123">&#124;     ReflectionDimension ReflectionDimension ','</span><span class="sxs-lookup"><span data-stu-id="51b1d-123">&#124;     ReflectionDimension ',' ReflectionDimension</span></span><br /><br /> <span data-ttu-id="51b1d-124">&#124;     NOTOKEN</span><span class="sxs-lookup"><span data-stu-id="51b1d-124">&#124;     NOTOKEN</span></span>|  
|<span data-ttu-id="51b1d-125">ReflectionEmitDimension: = ' *'</span><span class="sxs-lookup"><span data-stu-id="51b1d-125">ReflectionEmitDimension    :=   '*'</span></span><br /><br /> <span data-ttu-id="51b1d-126">&#124;     Číslo '..'</span><span class="sxs-lookup"><span data-stu-id="51b1d-126">&#124;     Number '..'</span></span> <span data-ttu-id="51b1d-127">Číslo</span><span class="sxs-lookup"><span data-stu-id="51b1d-127">Number</span></span><br /><br /> <span data-ttu-id="51b1d-128">&#124;     Číslo '...</span><span class="sxs-lookup"><span data-stu-id="51b1d-128">&#124;     Number '…'</span></span><br /><br /> <span data-ttu-id="51b1d-129">&#124;     ReflectionDimension ReflectionDimension ','</span><span class="sxs-lookup"><span data-stu-id="51b1d-129">&#124;     ReflectionDimension ',' ReflectionDimension</span></span><br /><br /> <span data-ttu-id="51b1d-130">&#124;     NOTOKEN</span><span class="sxs-lookup"><span data-stu-id="51b1d-130">&#124;     NOTOKEN</span></span>|  
|<span data-ttu-id="51b1d-131">Číslo: = [0-9] +</span><span class="sxs-lookup"><span data-stu-id="51b1d-131">Number                            :=   [0-9]+</span></span>|  
|<span data-ttu-id="51b1d-132">TypeName: = NamespaceTypeName</span><span class="sxs-lookup"><span data-stu-id="51b1d-132">TypeName                         :=   NamespaceTypeName</span></span><br /><br /> <span data-ttu-id="51b1d-133">&#124;     NamespaceTypeName AssemblyNameSpec ','</span><span class="sxs-lookup"><span data-stu-id="51b1d-133">&#124;     NamespaceTypeName ',' AssemblyNameSpec</span></span>|  
|<span data-ttu-id="51b1d-134">NamespaceTypeName: = NestedTypeName</span><span class="sxs-lookup"><span data-stu-id="51b1d-134">NamespaceTypeName        :=   NestedTypeName</span></span><br /><br /> <span data-ttu-id="51b1d-135">&#124;     NamespaceSpec '. " NestedTypeName</span><span class="sxs-lookup"><span data-stu-id="51b1d-135">&#124;     NamespaceSpec '.' NestedTypeName</span></span>|  
|<span data-ttu-id="51b1d-136">NestedTypeName: = IDENTIFIKÁTOR</span><span class="sxs-lookup"><span data-stu-id="51b1d-136">NestedTypeName               :=   IDENTIFIER</span></span><br /><br /> <span data-ttu-id="51b1d-137">&#124;     NestedTypeName IDENTIFIKÁTOR '+'</span><span class="sxs-lookup"><span data-stu-id="51b1d-137">&#124;     NestedTypeName '+' IDENTIFIER</span></span>|  
|<span data-ttu-id="51b1d-138">NamespaceSpec: = IDENTIFIKÁTOR</span><span class="sxs-lookup"><span data-stu-id="51b1d-138">NamespaceSpec                 :=   IDENTIFIER</span></span><br /><br /> <span data-ttu-id="51b1d-139">&#124;     NamespaceSpec '. " IDENTIFIKÁTOR</span><span class="sxs-lookup"><span data-stu-id="51b1d-139">&#124;     NamespaceSpec '.' IDENTIFIER</span></span>|  
|<span data-ttu-id="51b1d-140">AssemblyNameSpec: = IDENTIFIKÁTOR</span><span class="sxs-lookup"><span data-stu-id="51b1d-140">AssemblyNameSpec           :=   IDENTIFIER</span></span><br /><br /> <span data-ttu-id="51b1d-141">&#124;     IDENTIFIKÁTOR AssemblyProperties ','</span><span class="sxs-lookup"><span data-stu-id="51b1d-141">&#124;     IDENTIFIER ',' AssemblyProperties</span></span>|  
|<span data-ttu-id="51b1d-142">AssemblyProperties: = AssemblyProperty</span><span class="sxs-lookup"><span data-stu-id="51b1d-142">AssemblyProperties            :=   AssemblyProperty</span></span><br /><br /> <span data-ttu-id="51b1d-143">&#124;     AssemblyProperties AssemblyProperty ','</span><span class="sxs-lookup"><span data-stu-id="51b1d-143">&#124;     AssemblyProperties ',' AssemblyProperty</span></span>|  
|<span data-ttu-id="51b1d-144">AssemblyProperty: = AssemblyPropertyName '=' AssemblyPropertyValue</span><span class="sxs-lookup"><span data-stu-id="51b1d-144">AssemblyProperty              :=   AssemblyPropertyName '=' AssemblyPropertyValue</span></span>|  
  
## <a name="specifying-special-characters"></a><span data-ttu-id="51b1d-145">Zadání speciální znaky</span><span class="sxs-lookup"><span data-stu-id="51b1d-145">Specifying Special Characters</span></span>  
 <span data-ttu-id="51b1d-146">Název typu je IDENTIFIKÁTOR libovolný platný název určit pravidly jazyka.</span><span class="sxs-lookup"><span data-stu-id="51b1d-146">In a type name, IDENTIFIER is any valid name determined by the rules of a language.</span></span>  
  
 <span data-ttu-id="51b1d-147">Použít zpětné lomítko (\\) jako řídicí znak oddělit následující klíčová slova, pokud se používá jako součást IDENTIFIKÁTORU.</span><span class="sxs-lookup"><span data-stu-id="51b1d-147">Use the backslash (\\) as an escape character to separate the following tokens when used as part of IDENTIFIER.</span></span>  
  
|<span data-ttu-id="51b1d-148">Token</span><span class="sxs-lookup"><span data-stu-id="51b1d-148">Token</span></span>|<span data-ttu-id="51b1d-149">Význam</span><span class="sxs-lookup"><span data-stu-id="51b1d-149">Meaning</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="51b1d-150">\\,</span><span class="sxs-lookup"><span data-stu-id="51b1d-150">\\,</span></span>|<span data-ttu-id="51b1d-151">Oddělovač sestavení.</span><span class="sxs-lookup"><span data-stu-id="51b1d-151">Assembly separator.</span></span>|  
|\\+|<span data-ttu-id="51b1d-152">Vnořené typy oddělovače.</span><span class="sxs-lookup"><span data-stu-id="51b1d-152">Nested type separator.</span></span>|  
|\\&|<span data-ttu-id="51b1d-153">Typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="51b1d-153">Reference type.</span></span>|  
|\\*|<span data-ttu-id="51b1d-154">Typ ukazatele.</span><span class="sxs-lookup"><span data-stu-id="51b1d-154">Pointer type.</span></span>|  
|<span data-ttu-id="51b1d-155">\\[</span><span class="sxs-lookup"><span data-stu-id="51b1d-155">\\[</span></span>|<span data-ttu-id="51b1d-156">Pole dimenze oddělovač.</span><span class="sxs-lookup"><span data-stu-id="51b1d-156">Array dimension delimiter.</span></span>|  
|<span data-ttu-id="51b1d-157">\\]</span><span class="sxs-lookup"><span data-stu-id="51b1d-157">\\]</span></span>|<span data-ttu-id="51b1d-158">Pole dimenze oddělovač.</span><span class="sxs-lookup"><span data-stu-id="51b1d-158">Array dimension delimiter.</span></span>|  
|<span data-ttu-id="51b1d-159">\\.</span><span class="sxs-lookup"><span data-stu-id="51b1d-159">\\.</span></span>|<span data-ttu-id="51b1d-160">Použijte zpětné lomítko před dobou pouze v případě, že období se používá v specifikace pole.</span><span class="sxs-lookup"><span data-stu-id="51b1d-160">Use the backslash before a period only if the period is used in an array specification.</span></span> <span data-ttu-id="51b1d-161">Tečky v NamespaceSpec nepřebírají zpětné lomítko.</span><span class="sxs-lookup"><span data-stu-id="51b1d-161">Periods in NamespaceSpec do not take the backslash.</span></span>|  
|\\\|<span data-ttu-id="51b1d-162">Zpětné lomítko, v případě potřeby jako řetězcový literál.</span><span class="sxs-lookup"><span data-stu-id="51b1d-162">Backslash when needed as a string literal.</span></span>|  
  
 <span data-ttu-id="51b1d-163">Upozorňujeme, že v všechny součásti typ TypeSpec s výjimkou AssemblyNameSpec, jsou relevantní prostory.</span><span class="sxs-lookup"><span data-stu-id="51b1d-163">Note that in all TypeSpec components except AssemblyNameSpec, spaces are relevant.</span></span> <span data-ttu-id="51b1d-164">V AssemblyNameSpec jsou relevantní prostory před oddělovač ',', ale mezery po ',' oddělovač jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="51b1d-164">In the AssemblyNameSpec, spaces before the ',' separator are relevant, but spaces after the ',' separator are ignored.</span></span>  
  
 <span data-ttu-id="51b1d-165">Reflexe třídy, jako například <xref:System.Type.FullName%2A?displayProperty=nameWithType>, vrátí pozměnění název tak, aby vrácený název lze použít v volání <xref:System.Type.GetType%2A>jako v `MyType.GetType(myType.FullName)`.</span><span class="sxs-lookup"><span data-stu-id="51b1d-165">Reflection classes, such as <xref:System.Type.FullName%2A?displayProperty=nameWithType>, return the mangled name so that the returned name can be used in a call to <xref:System.Type.GetType%2A>, as in `MyType.GetType(myType.FullName)`.</span></span>  
  
 <span data-ttu-id="51b1d-166">Například může být plně kvalifikovaný název typu `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="51b1d-166">For example, the fully qualified name for a type might be `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span></span>  
  
 <span data-ttu-id="51b1d-167">Pokud byly oboru názvů `Ozzy.Out+Back`, pak na symbol plus musí předcházet zpětné lomítko.</span><span class="sxs-lookup"><span data-stu-id="51b1d-167">If the namespace were `Ozzy.Out+Back`, then the plus sign must be preceded by a backslash.</span></span> <span data-ttu-id="51b1d-168">Jinak by analyzátor toto jako oddělovač vnoření.</span><span class="sxs-lookup"><span data-stu-id="51b1d-168">Otherwise, the parser would interpret it as a nesting separator.</span></span> <span data-ttu-id="51b1d-169">Reflexe vysílá tento řetězec jako `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="51b1d-169">Reflection emits this string as `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span></span>  
  
## <a name="specifying-assembly-names"></a><span data-ttu-id="51b1d-170">Určení názvy sestavení</span><span class="sxs-lookup"><span data-stu-id="51b1d-170">Specifying Assembly Names</span></span>  
 <span data-ttu-id="51b1d-171">Minimální informace požadované specifikací název sestavení je textový název sestavení (IDENTIFIER).</span><span class="sxs-lookup"><span data-stu-id="51b1d-171">The minimum information required in an assembly name specification is the textual name (IDENTIFIER) of the assembly.</span></span> <span data-ttu-id="51b1d-172">IDENTIFIKÁTOR můžete provést pomocí seznam oddělený čárkami dvojic vlastnost/hodnota, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="51b1d-172">You can follow the IDENTIFIER by a comma-separated list of property/value pairs as described in the following table.</span></span> <span data-ttu-id="51b1d-173">IDENTIFIKÁTOR pojmenování by mělo vycházet pravidla pro pojmenovávání souborů.</span><span class="sxs-lookup"><span data-stu-id="51b1d-173">IDENTIFIER naming should follow the rules for file naming.</span></span> <span data-ttu-id="51b1d-174">IDENTIFIKÁTOR nerozlišuje velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="51b1d-174">The IDENTIFIER is case-insensitive.</span></span>  
  
|<span data-ttu-id="51b1d-175">Název vlastnosti</span><span class="sxs-lookup"><span data-stu-id="51b1d-175">Property name</span></span>|<span data-ttu-id="51b1d-176">Popis</span><span class="sxs-lookup"><span data-stu-id="51b1d-176">Description</span></span>|<span data-ttu-id="51b1d-177">Povolené hodnoty</span><span class="sxs-lookup"><span data-stu-id="51b1d-177">Allowable values</span></span>|  
|-------------------|-----------------|----------------------|  
|<span data-ttu-id="51b1d-178">**Verze**</span><span class="sxs-lookup"><span data-stu-id="51b1d-178">**Version**</span></span>|<span data-ttu-id="51b1d-179">Číslo verze sestavení</span><span class="sxs-lookup"><span data-stu-id="51b1d-179">Assembly version number</span></span>|<span data-ttu-id="51b1d-180">*Major.Minor.Build.Revision*, kde *hlavní*, *menší*, *sestavení*, a *revize* jsou celá čísla mezi 0 a 65535 (včetně).</span><span class="sxs-lookup"><span data-stu-id="51b1d-180">*Major.Minor.Build.Revision*, where *Major*, *Minor*, *Build*, and *Revision* are integers between 0 and 65535 inclusive.</span></span>|  
|<span data-ttu-id="51b1d-181">**PublicKey**</span><span class="sxs-lookup"><span data-stu-id="51b1d-181">**PublicKey**</span></span>|<span data-ttu-id="51b1d-182">Úplné veřejný klíč</span><span class="sxs-lookup"><span data-stu-id="51b1d-182">Full public key</span></span>|<span data-ttu-id="51b1d-183">Řetězec hodnotu úplné veřejný klíč v šestnáctkovém formátu.</span><span class="sxs-lookup"><span data-stu-id="51b1d-183">String value of full public key in hexadecimal format.</span></span> <span data-ttu-id="51b1d-184">Zadejte odkaz s hodnotou null (**nic** v jazyce Visual Basic) explicitně udávajících privátní sestavení.</span><span class="sxs-lookup"><span data-stu-id="51b1d-184">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|  
|<span data-ttu-id="51b1d-185">**PublicKeyToken**</span><span class="sxs-lookup"><span data-stu-id="51b1d-185">**PublicKeyToken**</span></span>|<span data-ttu-id="51b1d-186">Token veřejného klíče (8 bajtů hash veřejného klíče)</span><span class="sxs-lookup"><span data-stu-id="51b1d-186">Public key token (8-byte hash of the full public key)</span></span>|<span data-ttu-id="51b1d-187">Hodnota tokenu veřejného klíče v šestnáctkovém formátu řetězec.</span><span class="sxs-lookup"><span data-stu-id="51b1d-187">String value of public key token in hexadecimal format.</span></span> <span data-ttu-id="51b1d-188">Zadejte odkaz s hodnotou null (**nic** v jazyce Visual Basic) explicitně udávajících privátní sestavení.</span><span class="sxs-lookup"><span data-stu-id="51b1d-188">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|  
|<span data-ttu-id="51b1d-189">**Jazyková verze**</span><span class="sxs-lookup"><span data-stu-id="51b1d-189">**Culture**</span></span>|<span data-ttu-id="51b1d-190">Jazyková verze sestavení</span><span class="sxs-lookup"><span data-stu-id="51b1d-190">Assembly culture</span></span>|<span data-ttu-id="51b1d-191">Jazyková verze sestavení ve formátu RFC 1766, nebo "neutrální" pro sestavení nezávislé na jazyku (nonsatellite).</span><span class="sxs-lookup"><span data-stu-id="51b1d-191">Culture of the assembly in RFC-1766 format, or "neutral" for language-independent (nonsatellite) assemblies.</span></span>|  
|<span data-ttu-id="51b1d-192">**Vlastní**</span><span class="sxs-lookup"><span data-stu-id="51b1d-192">**Custom**</span></span>|<span data-ttu-id="51b1d-193">Vlastní binární rozsáhlý objekt (binární rozsáhlý OBJEKT).</span><span class="sxs-lookup"><span data-stu-id="51b1d-193">Custom binary large object (BLOB).</span></span> <span data-ttu-id="51b1d-194">To se aktuálně používá jenom v sestavení, které jsou generované [generátor (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="51b1d-194">This is currently used only in assemblies generated by the [Native Image Generator (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>|<span data-ttu-id="51b1d-195">Vlastní řetězec nástroje Generátor pro mezipaměť sestavení upozornit, že je nativních bitových kopií sestavení instaluje a proto má být nainstalován v mezipaměť nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="51b1d-195">Custom string used by the Native Image Generator tool to notify the assembly cache that the assembly being installed is a native image, and is therefore to be installed in the native image cache.</span></span> <span data-ttu-id="51b1d-196">Také nazývá zap řetězec.</span><span class="sxs-lookup"><span data-stu-id="51b1d-196">Also called a zap string.</span></span>|  
  
 <span data-ttu-id="51b1d-197">Následující příklad ukazuje **AssemblyName** pro jednoduše pojmenované sestavení s výchozí jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="51b1d-197">The following example shows an **AssemblyName** for a simply named assembly with default culture.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture=""   
```  
  
 <span data-ttu-id="51b1d-198">Následující příklad ukazuje plně zadaný odkaz pro silně pojmenované sestavení s jazykovou verzi "en".</span><span class="sxs-lookup"><span data-stu-id="51b1d-198">The following example shows a fully specified reference for a strongly named assembly with culture "en".</span></span>  
  
```csharp  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0   
```  
  
 <span data-ttu-id="51b1d-199">Následující příklady ukazují, částečně zadané **AssemblyName**, který může obsloužit silné nebo jednoduše pojmenované sestavení.</span><span class="sxs-lookup"><span data-stu-id="51b1d-199">The following examples each show a partially specified **AssemblyName**, which can be satisfied by either a strong or a simply named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto  
com.microsoft.crypto, Culture=""  
com.microsoft.crypto, Culture=en   
```  
  
 <span data-ttu-id="51b1d-200">Následující příklady ukazují, částečně zadané **AssemblyName**, které musí splnit jednoduše pojmenované sestavení.</span><span class="sxs-lookup"><span data-stu-id="51b1d-200">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a simply named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=null   
com.microsoft.crypto, Culture=en, PublicKeyToken=null  
```  
  
 <span data-ttu-id="51b1d-201">Následující příklady ukazují, částečně zadané **AssemblyName**, které musí splnit silně pojmenované sestavení.</span><span class="sxs-lookup"><span data-stu-id="51b1d-201">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a strongly named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0  
```  
  
## <a name="specifying-pointers"></a><span data-ttu-id="51b1d-202">Určení ukazatele</span><span class="sxs-lookup"><span data-stu-id="51b1d-202">Specifying Pointers</span></span>  
 <span data-ttu-id="51b1d-203">SimpleTypeSpec * představuje nespravovaný ukazatel.</span><span class="sxs-lookup"><span data-stu-id="51b1d-203">SimpleTypeSpec* represents an unmanaged pointer.</span></span> <span data-ttu-id="51b1d-204">Například ukazatel na typ MyType získáte pomocí `Type.GetType("MyType*")`.</span><span class="sxs-lookup"><span data-stu-id="51b1d-204">For example, to get a pointer to type MyType, use `Type.GetType("MyType*")`.</span></span> <span data-ttu-id="51b1d-205">Ukazatel na ukazatel na typ MyType získáte pomocí `Type.GetType("MyType**")`.</span><span class="sxs-lookup"><span data-stu-id="51b1d-205">To get a pointer to a pointer to type MyType, use `Type.GetType("MyType**")`.</span></span>  
  
## <a name="specifying-references"></a><span data-ttu-id="51b1d-206">Určení odkazy</span><span class="sxs-lookup"><span data-stu-id="51b1d-206">Specifying References</span></span>  
 <span data-ttu-id="51b1d-207">SimpleTypeSpec & reprezentuje spravované ukazatel nebo odkaz.</span><span class="sxs-lookup"><span data-stu-id="51b1d-207">SimpleTypeSpec & represents a managed pointer or reference.</span></span> <span data-ttu-id="51b1d-208">Například pokud chcete získat odkaz na typ MyType, použijte `Type.GetType("MyType &")`.</span><span class="sxs-lookup"><span data-stu-id="51b1d-208">For example, to get a reference to type MyType, use `Type.GetType("MyType &")`.</span></span> <span data-ttu-id="51b1d-209">Všimněte si, že na rozdíl od ukazatele, odkazy jsou omezeny na jedné úrovni.</span><span class="sxs-lookup"><span data-stu-id="51b1d-209">Note that unlike pointers, references are limited to one level.</span></span>  
  
## <a name="specifying-arrays"></a><span data-ttu-id="51b1d-210">Určení pole</span><span class="sxs-lookup"><span data-stu-id="51b1d-210">Specifying Arrays</span></span>  
 <span data-ttu-id="51b1d-211">V BNF – gramatika, ReflectionEmitDimension platí pouze pro neúplné typ definice načten pomocí <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="51b1d-211">In the BNF Grammar, ReflectionEmitDimension only applies to incomplete type definitions retrieved using <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="51b1d-212">Jsou neúplné typ definice <xref:System.Reflection.Emit.TypeBuilder> objekty, které jsou vytvářeny pomocí <xref:System.Reflection.Emit?displayProperty=nameWithType> , ale na kterém <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> nebyla volána.</span><span class="sxs-lookup"><span data-stu-id="51b1d-212">Incomplete type definitions are <xref:System.Reflection.Emit.TypeBuilder> objects constructed using <xref:System.Reflection.Emit?displayProperty=nameWithType> but on which <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> has not been called.</span></span> <span data-ttu-id="51b1d-213">ReflectionDimension umožňuje načíst všechny definice typu, která byla dokončena, který je typ, který byl načten.</span><span class="sxs-lookup"><span data-stu-id="51b1d-213">ReflectionDimension can be used to retrieve any type definition that has been completed, that is, a type that has been loaded.</span></span>  
  
 <span data-ttu-id="51b1d-214">Pole jsou přístupné v reflexe určení pořadí pole:</span><span class="sxs-lookup"><span data-stu-id="51b1d-214">Arrays are accessed in reflection by specifying the rank of the array:</span></span>  
  
-   <span data-ttu-id="51b1d-215">`Type.GetType("MyArray[]")`Získá pole jedním dimenze s 0 dolní mez.</span><span class="sxs-lookup"><span data-stu-id="51b1d-215">`Type.GetType("MyArray[]")` gets a single-dimension array with 0 lower bound.</span></span>  
  
-   <span data-ttu-id="51b1d-216">`Type.GetType("MyArray[*]")`Získá pole jedním dimenze s neznámou dolní mez.</span><span class="sxs-lookup"><span data-stu-id="51b1d-216">`Type.GetType("MyArray[*]")` gets a single-dimension array with unknown lower bound.</span></span>  
  
-   <span data-ttu-id="51b1d-217">`Type.GetType("MyArray[][]")`Získá pole dvourozměrná pole.</span><span class="sxs-lookup"><span data-stu-id="51b1d-217">`Type.GetType("MyArray[][]")` gets a two-dimensional array's array.</span></span>  
  
-   <span data-ttu-id="51b1d-218">`Type.GetType("MyArray[*,*]")`a `Type.GetType("MyArray[,]")` získá obdélníková dvourozměrná pole s neznámou dolní meze.</span><span class="sxs-lookup"><span data-stu-id="51b1d-218">`Type.GetType("MyArray[*,*]")` and `Type.GetType("MyArray[,]")` gets a rectangular two-dimensional array with unknown lower bounds.</span></span>  
  
 <span data-ttu-id="51b1d-219">Všimněte si, že se z modulu runtime hlediska, `MyArray[] != MyArray[*]`, ale pro vícerozměrná pole jsou ekvivalentní zápisy dva.</span><span class="sxs-lookup"><span data-stu-id="51b1d-219">Note that from a runtime point of view, `MyArray[] != MyArray[*]`, but for multidimensional arrays, the two notations are equivalent.</span></span> <span data-ttu-id="51b1d-220">To znamená `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` vyhodnotí jako **true**.</span><span class="sxs-lookup"><span data-stu-id="51b1d-220">That is, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` evaluates to **true**.</span></span>  
  
 <span data-ttu-id="51b1d-221">Pro **ModuleBuilder.GetType**, `MyArray[0..5]` označuje jeden dimenze pole s velikostí 6, nižší vázán 0.</span><span class="sxs-lookup"><span data-stu-id="51b1d-221">For **ModuleBuilder.GetType**, `MyArray[0..5]` indicates a single-dimension array with size 6, lower bound 0.</span></span> <span data-ttu-id="51b1d-222">`MyArray[4…]`Určuje pole dimenze jeden neznámý velikost a dolní hranice 4.</span><span class="sxs-lookup"><span data-stu-id="51b1d-222">`MyArray[4…]` indicates a single-dimension array of unknown size and lower bound 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51b1d-223">Viz také</span><span class="sxs-lookup"><span data-stu-id="51b1d-223">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 <xref:System.Reflection.Emit.ModuleBuilder>  
 <xref:System.Reflection.Emit.TypeBuilder>  
 <xref:System.Type.FullName%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="51b1d-224">Zobrazení informací o typu</span><span class="sxs-lookup"><span data-stu-id="51b1d-224">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
