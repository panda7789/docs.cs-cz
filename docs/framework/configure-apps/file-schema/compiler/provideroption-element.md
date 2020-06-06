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
ms.openlocfilehash: c8ba5b9a0680f5e5102c13eb5bb0c1904a168c07
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155398"
---
# <a name="provideroption-element"></a><span data-ttu-id="bc3b0-102">Element \<providerOption></span><span class="sxs-lookup"><span data-stu-id="bc3b0-102">\<providerOption> Element</span></span>
<span data-ttu-id="bc3b0-103">Určuje atributy verze kompilátoru pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="bc3b0-103">Specifies the compiler version attributes for a language provider.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<providerOption>**

## <a name="syntax"></a><span data-ttu-id="bc3b0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc3b0-104">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc3b0-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bc3b0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bc3b0-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bc3b0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc3b0-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="bc3b0-107">Attributes</span></span>  
  
|<span data-ttu-id="bc3b0-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="bc3b0-108">Attribute</span></span>|<span data-ttu-id="bc3b0-109">Popis</span><span class="sxs-lookup"><span data-stu-id="bc3b0-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="bc3b0-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="bc3b0-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="bc3b0-111">Určuje název možnosti. například "CompilerVersion".</span><span class="sxs-lookup"><span data-stu-id="bc3b0-111">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="bc3b0-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="bc3b0-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="bc3b0-113">Určuje hodnotu možnosti; například "v 3.5".</span><span class="sxs-lookup"><span data-stu-id="bc3b0-113">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc3b0-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bc3b0-114">Child Elements</span></span>  
 <span data-ttu-id="bc3b0-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="bc3b0-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc3b0-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bc3b0-116">Parent Elements</span></span>  
  
|<span data-ttu-id="bc3b0-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="bc3b0-117">Element</span></span>|<span data-ttu-id="bc3b0-118">Description</span><span class="sxs-lookup"><span data-stu-id="bc3b0-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc3b0-119">\<configuration>Objekt</span><span class="sxs-lookup"><span data-stu-id="bc3b0-119">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="bc3b0-120">Kořenový element v každém konfiguračním souboru, který je používán common language runtime a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bc3b0-120">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="bc3b0-121">\<system.codedom>Objekt</span><span class="sxs-lookup"><span data-stu-id="bc3b0-121">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="bc3b0-122">Určuje nastavení konfigurace kompilátoru pro dostupné poskytovatele jazyků.</span><span class="sxs-lookup"><span data-stu-id="bc3b0-122">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="bc3b0-123">\<compilers>Objekt</span><span class="sxs-lookup"><span data-stu-id="bc3b0-123">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="bc3b0-124">Kontejner pro prvky konfigurace kompilátoru; obsahuje nula nebo více `<compiler>` prvků.</span><span class="sxs-lookup"><span data-stu-id="bc3b0-124">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="bc3b0-125">\<compiler>Objekt</span><span class="sxs-lookup"><span data-stu-id="bc3b0-125">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="bc3b0-126">Určuje atributy konfigurace kompilátoru pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="bc3b0-126">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc3b0-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bc3b0-127">Remarks</span></span>  
 <span data-ttu-id="bc3b0-128">V .NET Framework verze 3,5 mohou poskytovatelé kódu Code Document Object Model (CodeDOM) podporovat možnosti specifické pro poskytovatele pomocí `<providerOption>` elementu.</span><span class="sxs-lookup"><span data-stu-id="bc3b0-128">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="bc3b0-129">.NET Framework 3,5 obsahuje aktualizované .NET Framework 2,0 sestavení a poskytuje nová 3,5 verze, která obsahuje sestavení, která obsahují nové typy.</span><span class="sxs-lookup"><span data-stu-id="bc3b0-129">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="bc3b0-130">Poskytovatelé kódu Microsoft C# a Visual Basic jsou obsaženi v sestaveních .NET Framework 2,0, ale byly aktualizovány pro podporu kompilátorů verze 3,5.</span><span class="sxs-lookup"><span data-stu-id="bc3b0-130">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="bc3b0-131">Ve výchozím nastavení Aktualizovaní poskytovatelé kódu generují kód pro kompilátory verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="bc3b0-131">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="bc3b0-132">Pomocí `<providerOption>` elementu můžete změnit cílovou verzi kompilátoru na 3,5.</span><span class="sxs-lookup"><span data-stu-id="bc3b0-132">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="bc3b0-133">Chcete-li to provést, zadejte "CompilerVersion" pro `name` atribut a "v 3.5" pro `value` atribut.</span><span class="sxs-lookup"><span data-stu-id="bc3b0-133">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="bc3b0-134">Číslo verze se musí nacházet s malým písmenem "v".</span><span class="sxs-lookup"><span data-stu-id="bc3b0-134">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="bc3b0-135">Specifikaci verze můžete vytvořit globální přidáním `<providerOption>` elementu do souboru .NET Framework 2,0 Machine. config nebo root web. config.</span><span class="sxs-lookup"><span data-stu-id="bc3b0-135">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="bc3b0-136">Pokud aktualizujete výchozí verzi kompilátoru na 3,5 v souboru Machine. config, můžete ji změnit na 2,0 na základě jednotlivých aplikací pomocí `<providerOption>` elementu v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="bc3b0-136">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="bc3b0-137">Implementátori poskytovatele kódu CodeDOM mohou zpracovat vlastní možnosti, a to poskytnutím konstruktoru, který přijímá `providerOptions` parametr typu <xref:System.Collections.Generic.IDictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="bc3b0-137">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc3b0-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc3b0-138">Example</span></span>  
 <span data-ttu-id="bc3b0-139">Následující příklad ukazuje, jak určit, že by měla být použita verze 3,5 poskytovatele kódu jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="bc3b0-139">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bc3b0-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc3b0-140">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="bc3b0-141">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="bc3b0-141">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="bc3b0-142">\<compilers>Objekt</span><span class="sxs-lookup"><span data-stu-id="bc3b0-142">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="bc3b0-143">Určení úplných názvů typů</span><span class="sxs-lookup"><span data-stu-id="bc3b0-143">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="bc3b0-144">[Element Compiler pro kompilátory pro kompilaci (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bc3b0-144">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
