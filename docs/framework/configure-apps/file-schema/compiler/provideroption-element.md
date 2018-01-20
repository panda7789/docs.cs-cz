---
title: "&lt;Hodnota providerOption&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
caps.latest.revision: "22"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f28b7b43f2f782744a0dbc81bd0b91bbbcd8abba
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltprovideroptiongt-element"></a><span data-ttu-id="5a5f0-102">&lt;Hodnota providerOption&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="5a5f0-102">&lt;providerOption&gt; Element</span></span>
<span data-ttu-id="5a5f0-103">Určuje verzi atributy kompilátoru jazyka zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-103">Specifies the compiler version attributes for a language provider.</span></span>  
  
 <span data-ttu-id="5a5f0-104">\<konfigurace elementu ></span><span class="sxs-lookup"><span data-stu-id="5a5f0-104">\<configuration Element></span></span>  
<span data-ttu-id="5a5f0-105">\<system.codedom Element></span><span class="sxs-lookup"><span data-stu-id="5a5f0-105">\<system.codedom Element></span></span>  
<span data-ttu-id="5a5f0-106">\<compilers Element></span><span class="sxs-lookup"><span data-stu-id="5a5f0-106">\<compilers Element></span></span>  
<span data-ttu-id="5a5f0-107">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="5a5f0-107">\<compiler> Element</span></span>  
<span data-ttu-id="5a5f0-108">\<Hodnota providerOption > elementu</span><span class="sxs-lookup"><span data-stu-id="5a5f0-108">\<providerOption> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a5f0-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a5f0-109">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a5f0-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5a5f0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5a5f0-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a5f0-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="5a5f0-112">Attributes</span></span>  
  
|<span data-ttu-id="5a5f0-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="5a5f0-113">Attribute</span></span>|<span data-ttu-id="5a5f0-114">Popis</span><span class="sxs-lookup"><span data-stu-id="5a5f0-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="5a5f0-115">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="5a5f0-116">Určuje název možnost; například "CompilerVersion".</span><span class="sxs-lookup"><span data-stu-id="5a5f0-116">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="5a5f0-117">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="5a5f0-118">Určuje hodnotu pro možnost; například "v3.5".</span><span class="sxs-lookup"><span data-stu-id="5a5f0-118">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a5f0-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5a5f0-119">Child Elements</span></span>  
 <span data-ttu-id="5a5f0-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="5a5f0-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a5f0-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5a5f0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5a5f0-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="5a5f0-122">Element</span></span>|<span data-ttu-id="5a5f0-123">Popis</span><span class="sxs-lookup"><span data-stu-id="5a5f0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a5f0-124">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="5a5f0-124">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="5a5f0-125">Kořenový element v každém konfiguračním souboru, který je používán common language runtime a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-125">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="5a5f0-126">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="5a5f0-126">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="5a5f0-127">Určuje kompilátor – nastavení konfigurace pro zprostředkovatele dostupný jazyk.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-127">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="5a5f0-128">\<compilers> Element</span><span class="sxs-lookup"><span data-stu-id="5a5f0-128">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="5a5f0-129">Kontejner pro kompilátor – elementy konfigurace; obsahuje nula nebo více `<compiler>` elementy.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-129">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="5a5f0-130">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="5a5f0-130">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="5a5f0-131">Kompilátor – konfigurační atributy Určuje jazyk zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-131">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a5f0-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a5f0-132">Remarks</span></span>  
 <span data-ttu-id="5a5f0-133">V rozhraní .NET Framework verze 3.5 zprostředkovatele kódu Code Document Object Model (CodeDOM) může podporovat možnosti specifický pro zprostředkovatele pomocí `<providerOption>` elementu.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-133">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="5a5f0-134">Rozhraní .NET Framework 3.5 zahrnuje aktualizované sestavení rozhraní .NET Framework 2.0 a poskytuje nové verze 3.5 sestavení, které obsahují nové typy.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-134">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="5a5f0-135">Kód zprostředkovatele Microsoft C# a Visual Basic jsou obsaženy v sestavení rozhraní .NET Framework 2.0, ale byly aktualizovány pro podporu kompilátory verze 3.5.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-135">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="5a5f0-136">Ve výchozím nastavení zprostředkovatele aktualizovaný kódu generovat kód pro kompilátory verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-136">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="5a5f0-137">Můžete použít `<providerOption>` elementu, který chcete změnit na cílovou verzi kompilátoru až 3.5.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-137">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="5a5f0-138">Chcete-li to provést, zadejte "CompilerVersion" pro `name` atribut a "v3.5" pro `value` atribut.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-138">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="5a5f0-139">Je nutné před číslo verze s malým "v".</span><span class="sxs-lookup"><span data-stu-id="5a5f0-139">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="5a5f0-140">Můžete provést specifikace verze globální přidáním `<providerOption>` element pro rozhraní .NET Framework 2.0 souboru Machine.config nebo v kořenovém souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-140">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="5a5f0-141">Pokud aktualizujete výchozí verze kompilátoru až 3.5 v souboru Machine.config, můžete ji změnit zpátky na 2.0 na základě jednotlivých aplikací pomocí `<providerOption>` element v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-141">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="5a5f0-142">Implementátory zprostředkovatele codeDOM kódu může zpracovat vlastní možnosti tím, že poskytuje konstruktor, který přebírá `providerOptions` parametr typu <xref:System.Collections.Generic.IDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-142">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a5f0-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a5f0-143">Example</span></span>  
 <span data-ttu-id="5a5f0-144">Následující příklad ukazuje, jak zadat této verze 3.5 zprostředkovatele kódu C# má být použita.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-144">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
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
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a5f0-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a5f0-145">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="5a5f0-146">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="5a5f0-146">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="5a5f0-147">\<compilers> Element</span><span class="sxs-lookup"><span data-stu-id="5a5f0-147">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [<span data-ttu-id="5a5f0-148">Určení úplných názvů typů</span><span class="sxs-lookup"><span data-stu-id="5a5f0-148">Specifying Fully Qualified Type Names</span></span>](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 [<span data-ttu-id="5a5f0-149">kompilátoru Element pro kompilátory pro kompilaci (schéma nastavení ASP.NET)</span><span class="sxs-lookup"><span data-stu-id="5a5f0-149">compiler Element for compilers for compilation (ASP.NET Settings Schema)</span></span>](http://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
