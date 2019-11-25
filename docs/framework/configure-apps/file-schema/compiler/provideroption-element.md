---
title: Element <providerOption>
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
ms.openlocfilehash: a6718173e84ecffc4ba0641f6e865e777aa6b1a4
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088677"
---
# <a name="provideroption-element"></a><span data-ttu-id="2bb1e-102">\<element > providerOption</span><span class="sxs-lookup"><span data-stu-id="2bb1e-102">\<providerOption> Element</span></span>
<span data-ttu-id="2bb1e-103">Určuje atributy verze kompilátoru pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="2bb1e-103">Specifies the compiler version attributes for a language provider.</span></span>  

<span data-ttu-id="2bb1e-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="2bb1e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2bb1e-105">&nbsp;&nbsp;[ **\<System. codedom >** ](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="2bb1e-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span></span>\
<span data-ttu-id="2bb1e-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kompilátory**](compilers-element.md) ></span><span class="sxs-lookup"><span data-stu-id="2bb1e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)</span></span>\
<span data-ttu-id="2bb1e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kompilátoru >** ](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="2bb1e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)</span></span>\
<span data-ttu-id="2bb1e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<providerOption >**</span><span class="sxs-lookup"><span data-stu-id="2bb1e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<providerOption>**</span></span>

## <a name="syntax"></a><span data-ttu-id="2bb1e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bb1e-109">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2bb1e-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2bb1e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2bb1e-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2bb1e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2bb1e-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="2bb1e-112">Attributes</span></span>  
  
|<span data-ttu-id="2bb1e-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="2bb1e-113">Attribute</span></span>|<span data-ttu-id="2bb1e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="2bb1e-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="2bb1e-115">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="2bb1e-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="2bb1e-116">Určuje název možnosti. například "CompilerVersion".</span><span class="sxs-lookup"><span data-stu-id="2bb1e-116">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="2bb1e-117">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="2bb1e-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="2bb1e-118">Určuje hodnotu možnosti; například "v 3.5".</span><span class="sxs-lookup"><span data-stu-id="2bb1e-118">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2bb1e-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2bb1e-119">Child Elements</span></span>  
 <span data-ttu-id="2bb1e-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="2bb1e-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2bb1e-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2bb1e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2bb1e-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="2bb1e-122">Element</span></span>|<span data-ttu-id="2bb1e-123">Popis</span><span class="sxs-lookup"><span data-stu-id="2bb1e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2bb1e-124">> element konfigurace \<</span><span class="sxs-lookup"><span data-stu-id="2bb1e-124">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="2bb1e-125">Kořenový element v každém konfiguračním souboru, který je používán common language runtime a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2bb1e-125">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="2bb1e-126">\<> element System. CodeDom</span><span class="sxs-lookup"><span data-stu-id="2bb1e-126">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="2bb1e-127">Určuje nastavení konfigurace kompilátoru pro dostupné poskytovatele jazyků.</span><span class="sxs-lookup"><span data-stu-id="2bb1e-127">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="2bb1e-128">> elementu \<kompilátorů</span><span class="sxs-lookup"><span data-stu-id="2bb1e-128">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="2bb1e-129">Kontejner pro prvky konfigurace kompilátoru; obsahuje nula nebo více `<compiler>` prvků.</span><span class="sxs-lookup"><span data-stu-id="2bb1e-129">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="2bb1e-130">\<element > kompilátoru</span><span class="sxs-lookup"><span data-stu-id="2bb1e-130">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="2bb1e-131">Určuje atributy konfigurace kompilátoru pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="2bb1e-131">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bb1e-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2bb1e-132">Remarks</span></span>  
 <span data-ttu-id="2bb1e-133">V .NET Framework verze 3,5 mohou poskytovatelé kódu Code Document Object Model (CodeDOM) podporovat možnosti specifické pro poskytovatele pomocí elementu `<providerOption>`.</span><span class="sxs-lookup"><span data-stu-id="2bb1e-133">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="2bb1e-134">.NET Framework 3,5 obsahuje aktualizované .NET Framework 2,0 sestavení a poskytuje nová 3,5 verze, která obsahuje sestavení, která obsahují nové typy.</span><span class="sxs-lookup"><span data-stu-id="2bb1e-134">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="2bb1e-135">Poskytovatelé C# kódu Microsoft a Visual Basic jsou obsaženi v sestaveních .NET Framework 2,0, ale byly aktualizovány pro podporu kompilátorů verze 3,5.</span><span class="sxs-lookup"><span data-stu-id="2bb1e-135">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="2bb1e-136">Ve výchozím nastavení Aktualizovaní poskytovatelé kódu generují kód pro kompilátory verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="2bb1e-136">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="2bb1e-137">Pomocí elementu `<providerOption>` můžete změnit cílovou verzi kompilátoru na 3,5.</span><span class="sxs-lookup"><span data-stu-id="2bb1e-137">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="2bb1e-138">To provedete tak, že zadáte "CompilerVersion" pro atribut `name` a "v 3.5" pro atribut `value`.</span><span class="sxs-lookup"><span data-stu-id="2bb1e-138">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="2bb1e-139">Číslo verze se musí nacházet s malým písmenem "v".</span><span class="sxs-lookup"><span data-stu-id="2bb1e-139">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="2bb1e-140">Specifikaci verze můžete vytvořit globální přidáním prvku `<providerOption>` do souboru .NET Framework 2,0 Machine. config nebo do kořenového souboru Web. config.</span><span class="sxs-lookup"><span data-stu-id="2bb1e-140">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="2bb1e-141">Pokud aktualizujete výchozí verzi kompilátoru na 3,5 v souboru Machine. config, můžete ji změnit zpět na 2,0 pro jednotlivé aplikace pomocí elementu `<providerOption>` v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="2bb1e-141">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="2bb1e-142">Implementátori poskytovatele kódu CodeDOM mohou zpracovat vlastní možnosti, a to poskytnutím konstruktoru, který přebírá `providerOptions` parametr typu <xref:System.Collections.Generic.IDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="2bb1e-142">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bb1e-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="2bb1e-143">Example</span></span>  
 <span data-ttu-id="2bb1e-144">Následující příklad ukazuje, jak určit, že by měla být použita C# verze 3,5 poskytovatele kódu.</span><span class="sxs-lookup"><span data-stu-id="2bb1e-144">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2bb1e-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2bb1e-145">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="2bb1e-146">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="2bb1e-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="2bb1e-147">> elementu \<kompilátorů</span><span class="sxs-lookup"><span data-stu-id="2bb1e-147">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="2bb1e-148">Určení úplných názvů typů</span><span class="sxs-lookup"><span data-stu-id="2bb1e-148">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="2bb1e-149">[Element Compiler pro kompilátory pro kompilaci (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2bb1e-149">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
