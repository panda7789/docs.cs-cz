---
title: Element <compiler>
ms.date: 08/14/2018
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
ms.openlocfilehash: 46676f25597f85596598d6f67c98930971cb0447
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088060"
---
# <a name="compiler-element"></a><span data-ttu-id="51d95-102">\<element > kompilátoru</span><span class="sxs-lookup"><span data-stu-id="51d95-102">\<compiler> Element</span></span>

<span data-ttu-id="51d95-103">Určuje atributy konfigurace kompilátoru pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="51d95-103">Specifies the compiler configuration attributes for a language provider.</span></span>

<span data-ttu-id="51d95-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="51d95-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="51d95-105">&nbsp;&nbsp;[ **\<System. codedom >** ](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="51d95-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span></span>\
<span data-ttu-id="51d95-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kompilátory**](compilers-element.md) ></span><span class="sxs-lookup"><span data-stu-id="51d95-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)</span></span>\
<span data-ttu-id="51d95-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<kompilátoru >**</span><span class="sxs-lookup"><span data-stu-id="51d95-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compiler>**</span></span>

## <a name="syntax"></a><span data-ttu-id="51d95-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51d95-108">Syntax</span></span>

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="51d95-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="51d95-109">Attributes and Elements</span></span>

<span data-ttu-id="51d95-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="51d95-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="51d95-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="51d95-111">Attributes</span></span>

|<span data-ttu-id="51d95-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="51d95-112">Attribute</span></span>|<span data-ttu-id="51d95-113">Popis</span><span class="sxs-lookup"><span data-stu-id="51d95-113">Description</span></span>|
|---------------|-----------------|
|`compilerOptions`|<span data-ttu-id="51d95-114">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="51d95-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="51d95-115">Určuje další argumenty specifické pro kompilátor pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="51d95-115">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="51d95-116">Hodnoty atributu `compilerOptions` jsou obvykle uvedeny v tématu Možnosti kompilátoru pro kompilátor.</span><span class="sxs-lookup"><span data-stu-id="51d95-116">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span>|
|`extension`|<span data-ttu-id="51d95-117">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="51d95-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="51d95-118">Poskytuje středníkem oddělený seznam přípon názvů souborů, které jsou používány zdrojovými soubory pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="51d95-118">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="51d95-119">Například ". cs".</span><span class="sxs-lookup"><span data-stu-id="51d95-119">For example, ".cs".</span></span>|
|`language`|<span data-ttu-id="51d95-120">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="51d95-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="51d95-121">Nabízí středníkem oddělený seznam názvů jazyků podporovaných poskytovatelem jazyka.</span><span class="sxs-lookup"><span data-stu-id="51d95-121">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="51d95-122">Například "c#; cs; CSharp".</span><span class="sxs-lookup"><span data-stu-id="51d95-122">For example, "c#;cs;csharp".</span></span>|
|`type`|<span data-ttu-id="51d95-123">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="51d95-123">Required attribute.</span></span><br /><br /> <span data-ttu-id="51d95-124">Určuje název typu poskytovatele jazyka, včetně názvu sestavení, které obsahuje implementaci poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="51d95-124">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="51d95-125">Název typu musí splňovat požadavky definované v části [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="51d95-125">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|
|`warningLevel`|<span data-ttu-id="51d95-126">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="51d95-126">Optional attribute.</span></span><br /><br /> <span data-ttu-id="51d95-127">Určuje výchozí úroveň upozornění kompilátoru; Určuje úroveň, na které poskytovatel jazyka považuje upozornění kompilace za chyby.</span><span class="sxs-lookup"><span data-stu-id="51d95-127">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="51d95-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="51d95-128">Child Elements</span></span>

|<span data-ttu-id="51d95-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="51d95-129">Element</span></span>|<span data-ttu-id="51d95-130">Popis</span><span class="sxs-lookup"><span data-stu-id="51d95-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="51d95-131">\<element > providerOption</span><span class="sxs-lookup"><span data-stu-id="51d95-131">\<providerOption> Element</span></span>](provideroption-element.md)|<span data-ttu-id="51d95-132">Určuje atributy verze kompilátoru pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="51d95-132">Specifies compiler version attributes for a language provider.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="51d95-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="51d95-133">Parent Elements</span></span>

|<span data-ttu-id="51d95-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="51d95-134">Element</span></span>|<span data-ttu-id="51d95-135">Popis</span><span class="sxs-lookup"><span data-stu-id="51d95-135">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="51d95-136">> element konfigurace \<</span><span class="sxs-lookup"><span data-stu-id="51d95-136">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="51d95-137">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="51d95-137">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|[<span data-ttu-id="51d95-138">\<> element System. CodeDom</span><span class="sxs-lookup"><span data-stu-id="51d95-138">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="51d95-139">Určuje nastavení konfigurace kompilátoru pro dostupné poskytovatele jazyků.</span><span class="sxs-lookup"><span data-stu-id="51d95-139">Specifies compiler configuration settings for available language providers.</span></span>|
|[<span data-ttu-id="51d95-140">> elementu \<kompilátorů</span><span class="sxs-lookup"><span data-stu-id="51d95-140">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="51d95-141">Kontejner pro prvky konfigurace kompilátoru; obsahuje nula nebo více `<compiler>` prvků.</span><span class="sxs-lookup"><span data-stu-id="51d95-141">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="51d95-142">Poznámky</span><span class="sxs-lookup"><span data-stu-id="51d95-142">Remarks</span></span>

<span data-ttu-id="51d95-143">Každý prvek `<compiler>` určuje atributy konfigurace kompilátoru pro konkrétního poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="51d95-143">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="51d95-144">Zprostředkovatel rozšiřuje třídu <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> pro konkrétní jazyk. element `<compiler>` definuje kompilátor a nastavení generátoru kódu pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="51d95-144">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>

<span data-ttu-id="51d95-145">.NET Framework definuje počáteční nastavení kompilátoru v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="51d95-145">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="51d95-146">Vývojáři a dodavatelé kompilátoru můžou přidat konfigurační nastavení pro novou implementaci <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="51d95-146">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="51d95-147">Použijte metodu <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> k programovému vytvoření výčtu poskytovatele jazyka a nastavení konfigurace kompilátoru v počítači.</span><span class="sxs-lookup"><span data-stu-id="51d95-147">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>

<span data-ttu-id="51d95-148">Prvky kompilátoru v souboru aplikace nebo webové konfigurace mohou doplnit nebo přepsat nastavení v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="51d95-148">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="51d95-149">Pokud je pro stejný název jazyka nebo stejnou příponu souboru nakonfigurovaná víc než jedna implementace zprostředkovatele, přepíše poslední odpovídající konfigurace všechny předchozí nakonfigurované zprostředkovatele pro daný název jazyka nebo příponu souboru.</span><span class="sxs-lookup"><span data-stu-id="51d95-149">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="51d95-150">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="51d95-150">Configuration File</span></span>

<span data-ttu-id="51d95-151">Tento element lze použít v konfiguračním souboru počítače a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="51d95-151">This element can be used in the machine configuration file and the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="51d95-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="51d95-152">Example</span></span>

<span data-ttu-id="51d95-153">Následující příklad ilustruje typický prvek konfigurace kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="51d95-153">The following example illustrates a typical compiler configuration element:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="51d95-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51d95-154">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="51d95-155">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="51d95-155">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="51d95-156">> elementu \<kompilátorů</span><span class="sxs-lookup"><span data-stu-id="51d95-156">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="51d95-157">Určení úplných názvů typů</span><span class="sxs-lookup"><span data-stu-id="51d95-157">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="51d95-158">[Element Compiler pro kompilátory pro kompilaci (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="51d95-158">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
