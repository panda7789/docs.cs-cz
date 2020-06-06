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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088060"
---
# <a name="compiler-element"></a><span data-ttu-id="ef901-102">Element \<compiler></span><span class="sxs-lookup"><span data-stu-id="ef901-102">\<compiler> Element</span></span>

<span data-ttu-id="ef901-103">Určuje atributy konfigurace kompilátoru pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="ef901-103">Specifies the compiler configuration attributes for a language provider.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compiler>**

## <a name="syntax"></a><span data-ttu-id="ef901-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef901-104">Syntax</span></span>

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ef901-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ef901-105">Attributes and Elements</span></span>

<span data-ttu-id="ef901-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ef901-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ef901-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="ef901-107">Attributes</span></span>

|<span data-ttu-id="ef901-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="ef901-108">Attribute</span></span>|<span data-ttu-id="ef901-109">Popis</span><span class="sxs-lookup"><span data-stu-id="ef901-109">Description</span></span>|
|---------------|-----------------|
|`compilerOptions`|<span data-ttu-id="ef901-110">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ef901-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ef901-111">Určuje další argumenty specifické pro kompilátor pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="ef901-111">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="ef901-112">Hodnoty pro `compilerOptions` atribut jsou obvykle uvedeny v tématu Možnosti kompilátoru pro kompilátor.</span><span class="sxs-lookup"><span data-stu-id="ef901-112">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span>|
|`extension`|<span data-ttu-id="ef901-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="ef901-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ef901-114">Poskytuje středníkem oddělený seznam přípon názvů souborů, které jsou používány zdrojovými soubory pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="ef901-114">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="ef901-115">Například ". cs".</span><span class="sxs-lookup"><span data-stu-id="ef901-115">For example, ".cs".</span></span>|
|`language`|<span data-ttu-id="ef901-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="ef901-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="ef901-117">Nabízí středníkem oddělený seznam názvů jazyků podporovaných poskytovatelem jazyka.</span><span class="sxs-lookup"><span data-stu-id="ef901-117">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="ef901-118">Například "c#; cs; CSharp".</span><span class="sxs-lookup"><span data-stu-id="ef901-118">For example, "c#;cs;csharp".</span></span>|
|`type`|<span data-ttu-id="ef901-119">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="ef901-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="ef901-120">Určuje název typu poskytovatele jazyka, včetně názvu sestavení, které obsahuje implementaci poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="ef901-120">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="ef901-121">Název typu musí splňovat požadavky definované v části [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="ef901-121">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|
|`warningLevel`|<span data-ttu-id="ef901-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ef901-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ef901-123">Určuje výchozí úroveň upozornění kompilátoru; Určuje úroveň, na které poskytovatel jazyka považuje upozornění kompilace za chyby.</span><span class="sxs-lookup"><span data-stu-id="ef901-123">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ef901-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ef901-124">Child Elements</span></span>

|<span data-ttu-id="ef901-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="ef901-125">Element</span></span>|<span data-ttu-id="ef901-126">Description</span><span class="sxs-lookup"><span data-stu-id="ef901-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef901-127">\<providerOption>Objekt</span><span class="sxs-lookup"><span data-stu-id="ef901-127">\<providerOption> Element</span></span>](provideroption-element.md)|<span data-ttu-id="ef901-128">Určuje atributy verze kompilátoru pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="ef901-128">Specifies compiler version attributes for a language provider.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ef901-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ef901-129">Parent Elements</span></span>

|<span data-ttu-id="ef901-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="ef901-130">Element</span></span>|<span data-ttu-id="ef901-131">Description</span><span class="sxs-lookup"><span data-stu-id="ef901-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef901-132">\<configuration>Objekt</span><span class="sxs-lookup"><span data-stu-id="ef901-132">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="ef901-133">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef901-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|[<span data-ttu-id="ef901-134">\<system.codedom>Objekt</span><span class="sxs-lookup"><span data-stu-id="ef901-134">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="ef901-135">Určuje nastavení konfigurace kompilátoru pro dostupné poskytovatele jazyků.</span><span class="sxs-lookup"><span data-stu-id="ef901-135">Specifies compiler configuration settings for available language providers.</span></span>|
|[<span data-ttu-id="ef901-136">\<compilers>Objekt</span><span class="sxs-lookup"><span data-stu-id="ef901-136">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="ef901-137">Kontejner pro prvky konfigurace kompilátoru; obsahuje nula nebo více `<compiler>` prvků.</span><span class="sxs-lookup"><span data-stu-id="ef901-137">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ef901-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ef901-138">Remarks</span></span>

<span data-ttu-id="ef901-139">Každý `<compiler>` prvek určuje atributy konfigurace kompilátoru pro konkrétního poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="ef901-139">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="ef901-140">Zprostředkovatel rozšiřuje <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> třídu pro určitý jazyk `<compiler>` . element definuje kompilátor a nastavení generátoru kódu pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="ef901-140">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>

<span data-ttu-id="ef901-141">.NET Framework definuje počáteční nastavení kompilátoru v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="ef901-141">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="ef901-142">Vývojáři a dodavatelé kompilátoru můžou přidat konfigurační nastavení pro novou <xref:System.CodeDom.Compiler.CodeDomProvider> implementaci.</span><span class="sxs-lookup"><span data-stu-id="ef901-142">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="ef901-143">Použijte <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metodu k programovému vytvoření výčtu poskytovatele jazyka a nastavení konfigurace kompilátoru v počítači.</span><span class="sxs-lookup"><span data-stu-id="ef901-143">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>

<span data-ttu-id="ef901-144">Prvky kompilátoru v souboru aplikace nebo webové konfigurace mohou doplnit nebo přepsat nastavení v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="ef901-144">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="ef901-145">Pokud je pro stejný název jazyka nebo stejnou příponu souboru nakonfigurovaná víc než jedna implementace zprostředkovatele, přepíše poslední odpovídající konfigurace všechny předchozí nakonfigurované zprostředkovatele pro daný název jazyka nebo příponu souboru.</span><span class="sxs-lookup"><span data-stu-id="ef901-145">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="ef901-146">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="ef901-146">Configuration File</span></span>

<span data-ttu-id="ef901-147">Tento element lze použít v konfiguračním souboru počítače a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="ef901-147">This element can be used in the machine configuration file and the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="ef901-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef901-148">Example</span></span>

<span data-ttu-id="ef901-149">Následující příklad ilustruje typický prvek konfigurace kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="ef901-149">The following example illustrates a typical compiler configuration element:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ef901-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef901-150">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="ef901-151">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="ef901-151">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ef901-152">\<compilers>Objekt</span><span class="sxs-lookup"><span data-stu-id="ef901-152">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="ef901-153">Určení úplných názvů typů</span><span class="sxs-lookup"><span data-stu-id="ef901-153">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="ef901-154">[Element Compiler pro kompilátory pro kompilaci (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ef901-154">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
