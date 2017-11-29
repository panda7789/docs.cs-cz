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
ms.openlocfilehash: 3a01a64ab8828104e8404f7d4efdd7b37eea373e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltprovideroptiongt-element"></a><span data-ttu-id="099de-102">&lt;Hodnota providerOption&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="099de-102">&lt;providerOption&gt; Element</span></span>
<span data-ttu-id="099de-103">Určuje verzi atributy kompilátoru jazyka zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="099de-103">Specifies the compiler version attributes for a language provider.</span></span>  
  
 <span data-ttu-id="099de-104">\<konfigurace elementu ></span><span class="sxs-lookup"><span data-stu-id="099de-104">\<configuration Element></span></span>  
<span data-ttu-id="099de-105">\<System.CodeDom – Element ></span><span class="sxs-lookup"><span data-stu-id="099de-105">\<system.codedom Element></span></span>  
<span data-ttu-id="099de-106">\<Kompilátory elementu ></span><span class="sxs-lookup"><span data-stu-id="099de-106">\<compilers Element></span></span>  
<span data-ttu-id="099de-107">\<kompilátoru > elementu</span><span class="sxs-lookup"><span data-stu-id="099de-107">\<compiler> Element</span></span>  
<span data-ttu-id="099de-108">\<Hodnota providerOption > elementu</span><span class="sxs-lookup"><span data-stu-id="099de-108">\<providerOption> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="099de-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="099de-109">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="099de-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="099de-110">Attributes and Elements</span></span>  
 <span data-ttu-id="099de-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="099de-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="099de-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="099de-112">Attributes</span></span>  
  
|<span data-ttu-id="099de-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="099de-113">Attribute</span></span>|<span data-ttu-id="099de-114">Popis</span><span class="sxs-lookup"><span data-stu-id="099de-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="099de-115">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="099de-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="099de-116">Určuje název možnost; například "CompilerVersion".</span><span class="sxs-lookup"><span data-stu-id="099de-116">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="099de-117">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="099de-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="099de-118">Určuje hodnotu pro možnost; například "v3.5".</span><span class="sxs-lookup"><span data-stu-id="099de-118">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="099de-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="099de-119">Child Elements</span></span>  
 <span data-ttu-id="099de-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="099de-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="099de-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="099de-121">Parent Elements</span></span>  
  
|<span data-ttu-id="099de-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="099de-122">Element</span></span>|<span data-ttu-id="099de-123">Popis</span><span class="sxs-lookup"><span data-stu-id="099de-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="099de-124">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="099de-124">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="099de-125">Kořenový element v každém konfiguračním souboru, který je používán common language runtime a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="099de-125">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="099de-126">\<System.CodeDom – > elementu</span><span class="sxs-lookup"><span data-stu-id="099de-126">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="099de-127">Určuje kompilátor – nastavení konfigurace pro zprostředkovatele dostupný jazyk.</span><span class="sxs-lookup"><span data-stu-id="099de-127">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="099de-128">\<Kompilátory > elementu</span><span class="sxs-lookup"><span data-stu-id="099de-128">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="099de-129">Kontejner pro kompilátor – elementy konfigurace; obsahuje nula nebo více `<compiler>` elementy.</span><span class="sxs-lookup"><span data-stu-id="099de-129">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="099de-130">\<kompilátoru > elementu</span><span class="sxs-lookup"><span data-stu-id="099de-130">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="099de-131">Kompilátor – konfigurační atributy Určuje jazyk zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="099de-131">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="099de-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="099de-132">Remarks</span></span>  
 <span data-ttu-id="099de-133">V rozhraní .NET Framework verze 3.5 zprostředkovatele kódu Code Document Object Model (CodeDOM) může podporovat možnosti specifický pro zprostředkovatele pomocí `<providerOption>` elementu.</span><span class="sxs-lookup"><span data-stu-id="099de-133">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="099de-134">Rozhraní .NET Framework 3.5 zahrnuje aktualizované sestavení rozhraní .NET Framework 2.0 a poskytuje nové verze 3.5 sestavení, které obsahují nové typy.</span><span class="sxs-lookup"><span data-stu-id="099de-134">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="099de-135">Kód zprostředkovatele Microsoft C# a Visual Basic jsou obsaženy v sestavení rozhraní .NET Framework 2.0, ale byly aktualizovány pro podporu kompilátory verze 3.5.</span><span class="sxs-lookup"><span data-stu-id="099de-135">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="099de-136">Ve výchozím nastavení zprostředkovatele aktualizovaný kódu generovat kód pro kompilátory verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="099de-136">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="099de-137">Můžete použít `<providerOption>` elementu, který chcete změnit na cílovou verzi kompilátoru až 3.5.</span><span class="sxs-lookup"><span data-stu-id="099de-137">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="099de-138">Chcete-li to provést, zadejte "CompilerVersion" pro `name` atribut a "v3.5" pro `value` atribut.</span><span class="sxs-lookup"><span data-stu-id="099de-138">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="099de-139">Je nutné před číslo verze s malým "v".</span><span class="sxs-lookup"><span data-stu-id="099de-139">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="099de-140">Můžete provést specifikace verze globální přidáním `<providerOption>` element pro rozhraní .NET Framework 2.0 souboru Machine.config nebo v kořenovém souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="099de-140">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="099de-141">Pokud aktualizujete výchozí verze kompilátoru až 3.5 v souboru Machine.config, můžete ji změnit zpátky na 2.0 na základě jednotlivých aplikací pomocí `<providerOption>` element v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="099de-141">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="099de-142">Implementátory zprostředkovatele codeDOM kódu může zpracovat vlastní možnosti tím, že poskytuje konstruktor, který přebírá `providerOptions` parametr typu <xref:System.Collections.Generic.IDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="099de-142">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="099de-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="099de-143">Example</span></span>  
 <span data-ttu-id="099de-144">Následující příklad ukazuje, jak zadat této verze 3.5 zprostředkovatele kódu C# má být použita.</span><span class="sxs-lookup"><span data-stu-id="099de-144">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="099de-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="099de-145">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="099de-146">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="099de-146">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="099de-147">\<Kompilátory > elementu</span><span class="sxs-lookup"><span data-stu-id="099de-147">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [<span data-ttu-id="099de-148">Určení úplné názvy typů</span><span class="sxs-lookup"><span data-stu-id="099de-148">Specifying Fully Qualified Type Names</span></span>](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 [<span data-ttu-id="099de-149">kompilátoru Element pro kompilátory pro kompilaci (schéma nastavení ASP.NET)</span><span class="sxs-lookup"><span data-stu-id="099de-149">compiler Element for compilers for compilation (ASP.NET Settings Schema)</span></span>](http://msdn.microsoft.com/en-us/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
