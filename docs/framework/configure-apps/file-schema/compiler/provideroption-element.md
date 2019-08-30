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
ms.openlocfilehash: 8d90364e34aa15bbd38e82ec70ec44616d7360f8
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70167671"
---
# <a name="provideroption-element"></a><span data-ttu-id="0351d-102">\<providerOption – element ></span><span class="sxs-lookup"><span data-stu-id="0351d-102">\<providerOption> Element</span></span>
<span data-ttu-id="0351d-103">Určuje atributy verze kompilátoru pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="0351d-103">Specifies the compiler version attributes for a language provider.</span></span>  
  
[<span data-ttu-id="0351d-104"> **\<> Konfigurace**</span><span class="sxs-lookup"><span data-stu-id="0351d-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="0351d-105">&nbsp;&nbsp;[ **\<System. CodeDom >** ](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="0351d-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span></span>  
<span data-ttu-id="0351d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> kompilátorů**](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="0351d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)</span></span>  
<span data-ttu-id="0351d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> kompilátoru**](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="0351d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)</span></span>  
<span data-ttu-id="0351d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<providerOption >**</span><span class="sxs-lookup"><span data-stu-id="0351d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<providerOption>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0351d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0351d-109">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0351d-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0351d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0351d-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0351d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0351d-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="0351d-112">Attributes</span></span>  
  
|<span data-ttu-id="0351d-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="0351d-113">Attribute</span></span>|<span data-ttu-id="0351d-114">Popis</span><span class="sxs-lookup"><span data-stu-id="0351d-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="0351d-115">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="0351d-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="0351d-116">Určuje název možnosti. například "CompilerVersion".</span><span class="sxs-lookup"><span data-stu-id="0351d-116">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="0351d-117">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="0351d-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="0351d-118">Určuje hodnotu možnosti; například "v 3.5".</span><span class="sxs-lookup"><span data-stu-id="0351d-118">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0351d-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0351d-119">Child Elements</span></span>  
 <span data-ttu-id="0351d-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="0351d-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0351d-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0351d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0351d-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="0351d-122">Element</span></span>|<span data-ttu-id="0351d-123">Popis</span><span class="sxs-lookup"><span data-stu-id="0351d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0351d-124">\<Element > Konfigurace</span><span class="sxs-lookup"><span data-stu-id="0351d-124">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="0351d-125">Kořenový element v každém konfiguračním souboru, který je používán common language runtime a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0351d-125">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="0351d-126">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="0351d-126">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="0351d-127">Určuje nastavení konfigurace kompilátoru pro dostupné poskytovatele jazyků.</span><span class="sxs-lookup"><span data-stu-id="0351d-127">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="0351d-128">\<kompilátory > element</span><span class="sxs-lookup"><span data-stu-id="0351d-128">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="0351d-129">Kontejner pro prvky konfigurace kompilátoru; obsahuje nula nebo více `<compiler>` prvků.</span><span class="sxs-lookup"><span data-stu-id="0351d-129">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="0351d-130">\<> – element kompilátoru</span><span class="sxs-lookup"><span data-stu-id="0351d-130">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="0351d-131">Určuje atributy konfigurace kompilátoru pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="0351d-131">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0351d-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0351d-132">Remarks</span></span>  
 <span data-ttu-id="0351d-133">V .NET Framework verze 3,5 mohou poskytovatelé kódu Code Document Object Model (CodeDOM) podporovat možnosti specifické pro poskytovatele pomocí `<providerOption>` elementu.</span><span class="sxs-lookup"><span data-stu-id="0351d-133">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="0351d-134">.NET Framework 3,5 obsahuje aktualizované .NET Framework 2,0 sestavení a poskytuje nová 3,5 verze, která obsahuje sestavení, která obsahují nové typy.</span><span class="sxs-lookup"><span data-stu-id="0351d-134">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="0351d-135">Poskytovatelé C# kódu Microsoft a Visual Basic jsou obsaženi v sestaveních .NET Framework 2,0, ale byly aktualizovány pro podporu kompilátorů verze 3,5.</span><span class="sxs-lookup"><span data-stu-id="0351d-135">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="0351d-136">Ve výchozím nastavení Aktualizovaní poskytovatelé kódu generují kód pro kompilátory verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="0351d-136">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="0351d-137">Pomocí `<providerOption>` elementu můžete změnit cílovou verzi kompilátoru na 3,5.</span><span class="sxs-lookup"><span data-stu-id="0351d-137">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="0351d-138">Chcete-li to provést, zadejte "CompilerVersion" `name` pro atribut a "v 3.5" `value` pro atribut.</span><span class="sxs-lookup"><span data-stu-id="0351d-138">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="0351d-139">Číslo verze se musí nacházet s malým písmenem "v".</span><span class="sxs-lookup"><span data-stu-id="0351d-139">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="0351d-140">Specifikaci verze můžete vytvořit globální přidáním `<providerOption>` elementu do souboru .NET Framework 2,0 Machine. config nebo root web. config.</span><span class="sxs-lookup"><span data-stu-id="0351d-140">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="0351d-141">Pokud aktualizujete výchozí verzi kompilátoru na 3,5 v souboru Machine. config, můžete ji změnit na 2,0 na základě jednotlivých aplikací pomocí `<providerOption>` elementu v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="0351d-141">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="0351d-142">Implementátori poskytovatele kódu CodeDOM mohou zpracovat vlastní možnosti, a to poskytnutím konstruktoru, `providerOptions` který přijímá parametr <xref:System.Collections.Generic.IDictionary%602>typu.</span><span class="sxs-lookup"><span data-stu-id="0351d-142">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0351d-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="0351d-143">Example</span></span>  
 <span data-ttu-id="0351d-144">Následující příklad ukazuje, jak určit, že by měla být použita C# verze 3,5 poskytovatele kódu.</span><span class="sxs-lookup"><span data-stu-id="0351d-144">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0351d-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0351d-145">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="0351d-146">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="0351d-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0351d-147">\<kompilátory > element</span><span class="sxs-lookup"><span data-stu-id="0351d-147">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="0351d-148">Určení úplných názvů typů</span><span class="sxs-lookup"><span data-stu-id="0351d-148">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="0351d-149">[Element Compiler pro kompilátory pro kompilaci (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0351d-149">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
