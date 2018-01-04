---
title: "&lt;kompilátoru&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 2ef50301a5188193cc13cd0e657f53593ef0d93e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltcompilergt-element"></a><span data-ttu-id="2c387-102">&lt;kompilátoru&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="2c387-102">&lt;compiler&gt; Element</span></span>
<span data-ttu-id="2c387-103">Kompilátor – konfigurační atributy Určuje jazyk zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="2c387-103">Specifies the compiler configuration attributes for a language provider.</span></span>  
  
 <span data-ttu-id="2c387-104">\<konfigurace elementu ></span><span class="sxs-lookup"><span data-stu-id="2c387-104">\<configuration Element></span></span>  
<span data-ttu-id="2c387-105">\<System.CodeDom – Element ></span><span class="sxs-lookup"><span data-stu-id="2c387-105">\<system.codedom Element></span></span>  
<span data-ttu-id="2c387-106">\<Kompilátory elementu ></span><span class="sxs-lookup"><span data-stu-id="2c387-106">\<compilers Element></span></span>  
<span data-ttu-id="2c387-107">\<kompilátoru > elementu</span><span class="sxs-lookup"><span data-stu-id="2c387-107">\<compiler> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c387-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c387-108">Syntax</span></span>  
  
```xml  
<compiler  
  language="languageName[;...;...]"  
  extension="fileExtension[;...;...]"  
  type="typeName, assemblyName"  
  warningLevel="number"  
  compilerOptions="option1 option2"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c387-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2c387-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2c387-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2c387-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c387-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="2c387-111">Attributes</span></span>  
  
|<span data-ttu-id="2c387-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="2c387-112">Attribute</span></span>|<span data-ttu-id="2c387-113">Popis</span><span class="sxs-lookup"><span data-stu-id="2c387-113">Description</span></span>|  
|---------------|-----------------|  
|`compilerOptions`|<span data-ttu-id="2c387-114">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="2c387-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="2c387-115">Určuje další argumenty kompilátoru specifické pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="2c387-115">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="2c387-116">Hodnoty `compilerOptions` atribut jsou většinou najdete v tématu možnosti kompilátoru pro kompilátor.</span><span class="sxs-lookup"><span data-stu-id="2c387-116">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span> <span data-ttu-id="2c387-117">V dokumentaci sady Visual Studio 2005 můžete vyhledat možnosti pro kompilátor tak, že vyhledá "– možnosti kompilátoru" v indexu.</span><span class="sxs-lookup"><span data-stu-id="2c387-117">In the Visual Studio 2005 documentation, you can locate the options for the compiler by looking for "compiler options" in the index.</span></span>|  
|`extension`|<span data-ttu-id="2c387-118">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="2c387-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="2c387-119">Poskytuje středníky oddělený seznam přípon názvů souborů, používá zdrojové soubory pro jazyk zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="2c387-119">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="2c387-120">Například ".cs".</span><span class="sxs-lookup"><span data-stu-id="2c387-120">For example, ".cs".</span></span>|  
|`language`|<span data-ttu-id="2c387-121">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="2c387-121">Required attribute.</span></span><br /><br /> <span data-ttu-id="2c387-122">Poskytuje středníky oddělený seznam názvů jazyka zprostředkovatel jazyk.</span><span class="sxs-lookup"><span data-stu-id="2c387-122">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="2c387-123">Například "c#; cs; csharp".</span><span class="sxs-lookup"><span data-stu-id="2c387-123">For example, "c#;cs;csharp".</span></span>|  
|`type`|<span data-ttu-id="2c387-124">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="2c387-124">Required attribute.</span></span><br /><br /> <span data-ttu-id="2c387-125">Určuje název typu zprostředkovatele jazyk, včetně název sestavení obsahujícího implementaci zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="2c387-125">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="2c387-126">Název typu musí splňovat požadavky definované v [určení plně kvalifikované názvy typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="2c387-126">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`warningLevel`|<span data-ttu-id="2c387-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="2c387-127">Optional attribute.</span></span><br /><br /> <span data-ttu-id="2c387-128">Určuje úroveň pro upozornění kompilátoru výchozí; Určuje úroveň, kdy zprostředkovatel jazyka zpracovává kompilace upozornění jako chyby.</span><span class="sxs-lookup"><span data-stu-id="2c387-128">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c387-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2c387-129">Child Elements</span></span>  
  
|<span data-ttu-id="2c387-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="2c387-130">Element</span></span>|<span data-ttu-id="2c387-131">Popis</span><span class="sxs-lookup"><span data-stu-id="2c387-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c387-132">\<Hodnota providerOption > elementu</span><span class="sxs-lookup"><span data-stu-id="2c387-132">\<providerOption> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|<span data-ttu-id="2c387-133">Určuje atributy verze kompilátoru jazyka zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="2c387-133">Specifies compiler version attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2c387-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2c387-134">Parent Elements</span></span>  
  
|<span data-ttu-id="2c387-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="2c387-135">Element</span></span>|<span data-ttu-id="2c387-136">Popis</span><span class="sxs-lookup"><span data-stu-id="2c387-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c387-137">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="2c387-137">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="2c387-138">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2c387-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="2c387-139">\<System.CodeDom – > elementu</span><span class="sxs-lookup"><span data-stu-id="2c387-139">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="2c387-140">Určuje kompilátor – nastavení konfigurace pro zprostředkovatele dostupný jazyk.</span><span class="sxs-lookup"><span data-stu-id="2c387-140">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="2c387-141">\<Kompilátory > elementu</span><span class="sxs-lookup"><span data-stu-id="2c387-141">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="2c387-142">Kontejner pro kompilátor – elementy konfigurace; obsahuje nula nebo více `<compiler>` elementy.</span><span class="sxs-lookup"><span data-stu-id="2c387-142">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c387-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c387-143">Remarks</span></span>  
 <span data-ttu-id="2c387-144">Každý `<compiler>` element určuje kompilátor – konfigurační atributy pro konkrétní jazyk zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="2c387-144">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="2c387-145">Zprostředkovatel rozšiřuje <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> třídy pro konkrétní jazyk; `<compiler>` element definuje kompilátoru a nastavení generátor kódu pro jazyk zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="2c387-145">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>  
  
 <span data-ttu-id="2c387-146">Rozhraní .NET Framework definuje nastavení počáteční kompilátoru v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="2c387-146">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="2c387-147">Vývojářům a dodavatelům kompilátoru můžete přidat nastavení konfigurace pro novou <xref:System.CodeDom.Compiler.CodeDomProvider> implementace.</span><span class="sxs-lookup"><span data-stu-id="2c387-147">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="2c387-148">Použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metoda prostřednictvím kódu programu výčet zprostředkovatele a kompilátoru konfigurace nastavení jazyka v počítači.</span><span class="sxs-lookup"><span data-stu-id="2c387-148">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
 <span data-ttu-id="2c387-149">Kompilátor – elementy v aplikaci nebo soubor webové konfigurace můžete doplnit nebo přepsat nastavení v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="2c387-149">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="2c387-150">Pokud je více než jednu implementaci zprostředkovatele je nakonfigurován pro stejný název jazyka a stejnou příponu souboru, přepíše poslední odpovídající konfigurace zprostředkovatelů předchozí nakonfigurovaný pro tento jazyk název nebo příponu souboru.</span><span class="sxs-lookup"><span data-stu-id="2c387-150">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="2c387-151">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="2c387-151">Configuration File</span></span>  
 <span data-ttu-id="2c387-152">Tento element lze v konfiguračním souboru počítače a konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="2c387-152">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c387-153">Příklad</span><span class="sxs-lookup"><span data-stu-id="2c387-153">Example</span></span>  
 <span data-ttu-id="2c387-154">Následující příklad ukazuje prvek typické kompilátoru konfigurace.</span><span class="sxs-lookup"><span data-stu-id="2c387-154">The following example illustrates a typical compiler configuration element.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler  
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=2.0.3600.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2c387-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c387-155">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="2c387-156">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="2c387-156">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="2c387-157">\<Kompilátory > elementu</span><span class="sxs-lookup"><span data-stu-id="2c387-157">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [<span data-ttu-id="2c387-158">Určení úplných názvů typů</span><span class="sxs-lookup"><span data-stu-id="2c387-158">Specifying Fully Qualified Type Names</span></span>](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 [<span data-ttu-id="2c387-159">kompilátoru Element pro kompilátory pro kompilaci (schéma nastavení ASP.NET)</span><span class="sxs-lookup"><span data-stu-id="2c387-159">compiler Element for compilers for compilation (ASP.NET Settings Schema)</span></span>](http://msdn.microsoft.com/en-us/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
