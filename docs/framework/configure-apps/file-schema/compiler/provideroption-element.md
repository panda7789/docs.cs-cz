---
title: '&lt;Hodnota providerOption&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fa3410cc2c8812c59528676bfad6cd7e887c5f73
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746394"
---
# <a name="ltprovideroptiongt-element"></a><span data-ttu-id="d6418-102">&lt;Hodnota providerOption&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="d6418-102">&lt;providerOption&gt; Element</span></span>
<span data-ttu-id="d6418-103">Určuje verzi atributy kompilátoru jazyka zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="d6418-103">Specifies the compiler version attributes for a language provider.</span></span>  
  
 <span data-ttu-id="d6418-104">\<konfigurace elementu ></span><span class="sxs-lookup"><span data-stu-id="d6418-104">\<configuration Element></span></span>  
<span data-ttu-id="d6418-105">\<system.codedom Element></span><span class="sxs-lookup"><span data-stu-id="d6418-105">\<system.codedom Element></span></span>  
<span data-ttu-id="d6418-106">\<Kompilátory elementu ></span><span class="sxs-lookup"><span data-stu-id="d6418-106">\<compilers Element></span></span>  
<span data-ttu-id="d6418-107">\<kompilátoru > elementu</span><span class="sxs-lookup"><span data-stu-id="d6418-107">\<compiler> Element</span></span>  
<span data-ttu-id="d6418-108">\<Hodnota providerOption > elementu</span><span class="sxs-lookup"><span data-stu-id="d6418-108">\<providerOption> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6418-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6418-109">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6418-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d6418-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d6418-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d6418-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6418-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="d6418-112">Attributes</span></span>  
  
|<span data-ttu-id="d6418-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="d6418-113">Attribute</span></span>|<span data-ttu-id="d6418-114">Popis</span><span class="sxs-lookup"><span data-stu-id="d6418-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="d6418-115">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="d6418-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="d6418-116">Určuje název možnost; například "CompilerVersion".</span><span class="sxs-lookup"><span data-stu-id="d6418-116">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="d6418-117">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="d6418-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="d6418-118">Určuje hodnotu pro možnost; například "v3.5".</span><span class="sxs-lookup"><span data-stu-id="d6418-118">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6418-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d6418-119">Child Elements</span></span>  
 <span data-ttu-id="d6418-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="d6418-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d6418-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d6418-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d6418-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="d6418-122">Element</span></span>|<span data-ttu-id="d6418-123">Popis</span><span class="sxs-lookup"><span data-stu-id="d6418-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6418-124">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="d6418-124">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="d6418-125">Kořenový element v každém konfiguračním souboru, který je používán common language runtime a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d6418-125">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="d6418-126">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="d6418-126">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="d6418-127">Určuje kompilátor – nastavení konfigurace pro zprostředkovatele dostupný jazyk.</span><span class="sxs-lookup"><span data-stu-id="d6418-127">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="d6418-128">\<Kompilátory > elementu</span><span class="sxs-lookup"><span data-stu-id="d6418-128">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="d6418-129">Kontejner pro kompilátor – elementy konfigurace; obsahuje nula nebo více `<compiler>` elementy.</span><span class="sxs-lookup"><span data-stu-id="d6418-129">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="d6418-130">\<kompilátoru > elementu</span><span class="sxs-lookup"><span data-stu-id="d6418-130">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="d6418-131">Kompilátor – konfigurační atributy Určuje jazyk zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="d6418-131">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6418-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6418-132">Remarks</span></span>  
 <span data-ttu-id="d6418-133">V rozhraní .NET Framework verze 3.5 zprostředkovatele kódu Code Document Object Model (CodeDOM) může podporovat možnosti specifický pro zprostředkovatele pomocí `<providerOption>` elementu.</span><span class="sxs-lookup"><span data-stu-id="d6418-133">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="d6418-134">Rozhraní .NET Framework 3.5 zahrnuje aktualizované sestavení rozhraní .NET Framework 2.0 a poskytuje nové verze 3.5 sestavení, které obsahují nové typy.</span><span class="sxs-lookup"><span data-stu-id="d6418-134">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="d6418-135">Kód zprostředkovatele Microsoft C# a Visual Basic jsou obsaženy v sestavení rozhraní .NET Framework 2.0, ale byly aktualizovány pro podporu kompilátory verze 3.5.</span><span class="sxs-lookup"><span data-stu-id="d6418-135">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="d6418-136">Ve výchozím nastavení zprostředkovatele aktualizovaný kódu generovat kód pro kompilátory verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="d6418-136">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="d6418-137">Můžete použít `<providerOption>` elementu, který chcete změnit na cílovou verzi kompilátoru až 3.5.</span><span class="sxs-lookup"><span data-stu-id="d6418-137">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="d6418-138">Chcete-li to provést, zadejte "CompilerVersion" pro `name` atribut a "v3.5" pro `value` atribut.</span><span class="sxs-lookup"><span data-stu-id="d6418-138">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="d6418-139">Je nutné před číslo verze s malým "v".</span><span class="sxs-lookup"><span data-stu-id="d6418-139">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="d6418-140">Můžete provést specifikace verze globální přidáním `<providerOption>` element pro rozhraní .NET Framework 2.0 souboru Machine.config nebo v kořenovém souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="d6418-140">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="d6418-141">Pokud aktualizujete výchozí verze kompilátoru až 3.5 v souboru Machine.config, můžete ji změnit zpátky na 2.0 na základě jednotlivých aplikací pomocí `<providerOption>` element v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="d6418-141">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="d6418-142">Implementátory zprostředkovatele codeDOM kódu může zpracovat vlastní možnosti tím, že poskytuje konstruktor, který přebírá `providerOptions` parametr typu <xref:System.Collections.Generic.IDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="d6418-142">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6418-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6418-143">Example</span></span>  
 <span data-ttu-id="d6418-144">Následující příklad ukazuje, jak zadat této verze 3.5 zprostředkovatele kódu C# má být použita.</span><span class="sxs-lookup"><span data-stu-id="d6418-144">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d6418-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6418-145">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="d6418-146">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="d6418-146">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="d6418-147">\<Kompilátory > elementu</span><span class="sxs-lookup"><span data-stu-id="d6418-147">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [<span data-ttu-id="d6418-148">Určení úplných názvů typů</span><span class="sxs-lookup"><span data-stu-id="d6418-148">Specifying Fully Qualified Type Names</span></span>](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 [<span data-ttu-id="d6418-149">kompilátoru Element pro kompilátory pro kompilaci (schéma nastavení ASP.NET)</span><span class="sxs-lookup"><span data-stu-id="d6418-149">compiler Element for compilers for compilation (ASP.NET Settings Schema)</span></span>](http://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
