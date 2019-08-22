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
ms.openlocfilehash: 80eea3373e2f4b7e45ebeb31dd6552ea02c109e1
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659734"
---
# <a name="compiler-element"></a><span data-ttu-id="f2f7c-102">\<> – element kompilátoru</span><span class="sxs-lookup"><span data-stu-id="f2f7c-102">\<compiler> Element</span></span>

<span data-ttu-id="f2f7c-103">Určuje atributy konfigurace kompilátoru pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-103">Specifies the compiler configuration attributes for a language provider.</span></span>

<span data-ttu-id="f2f7c-104">\<element konfigurace > \<element System. CodeDom > \<elementu compilers > \<elementu kompilátoru ></span><span class="sxs-lookup"><span data-stu-id="f2f7c-104">\<configuration Element> \<system.codedom Element> \<compilers Element> \<compiler> Element</span></span>

## <a name="syntax"></a><span data-ttu-id="f2f7c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2f7c-105">Syntax</span></span>

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f2f7c-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f2f7c-106">Attributes and Elements</span></span>

<span data-ttu-id="f2f7c-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f2f7c-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="f2f7c-108">Attributes</span></span>

|<span data-ttu-id="f2f7c-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="f2f7c-109">Attribute</span></span>|<span data-ttu-id="f2f7c-110">Popis</span><span class="sxs-lookup"><span data-stu-id="f2f7c-110">Description</span></span>|
|---------------|-----------------|
|`compilerOptions`|<span data-ttu-id="f2f7c-111">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f2f7c-112">Určuje další argumenty specifické pro kompilátor pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-112">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="f2f7c-113">Hodnoty pro `compilerOptions` atribut jsou obvykle uvedeny v tématu Možnosti kompilátoru pro kompilátor.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-113">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span>|
|`extension`|<span data-ttu-id="f2f7c-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="f2f7c-115">Poskytuje středníkem oddělený seznam přípon názvů souborů, které jsou používány zdrojovými soubory pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-115">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="f2f7c-116">Například ". cs".</span><span class="sxs-lookup"><span data-stu-id="f2f7c-116">For example, ".cs".</span></span>|
|`language`|<span data-ttu-id="f2f7c-117">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="f2f7c-118">Nabízí středníkem oddělený seznam názvů jazyků podporovaných poskytovatelem jazyka.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-118">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="f2f7c-119">Například "c#; cs; CSharp".</span><span class="sxs-lookup"><span data-stu-id="f2f7c-119">For example, "c#;cs;csharp".</span></span>|
|`type`|<span data-ttu-id="f2f7c-120">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="f2f7c-121">Určuje název typu poskytovatele jazyka, včetně názvu sestavení, které obsahuje implementaci poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-121">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="f2f7c-122">Název typu musí splňovat požadavky definované v části [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="f2f7c-122">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|
|`warningLevel`|<span data-ttu-id="f2f7c-123">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f2f7c-124">Určuje výchozí úroveň upozornění kompilátoru; Určuje úroveň, na které poskytovatel jazyka považuje upozornění kompilace za chyby.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-124">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="f2f7c-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f2f7c-125">Child Elements</span></span>

|<span data-ttu-id="f2f7c-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="f2f7c-126">Element</span></span>|<span data-ttu-id="f2f7c-127">Popis</span><span class="sxs-lookup"><span data-stu-id="f2f7c-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2f7c-128">\<providerOption – element ></span><span class="sxs-lookup"><span data-stu-id="f2f7c-128">\<providerOption> Element</span></span>](provideroption-element.md)|<span data-ttu-id="f2f7c-129">Určuje atributy verze kompilátoru pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-129">Specifies compiler version attributes for a language provider.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f2f7c-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f2f7c-130">Parent Elements</span></span>

|<span data-ttu-id="f2f7c-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="f2f7c-131">Element</span></span>|<span data-ttu-id="f2f7c-132">Popis</span><span class="sxs-lookup"><span data-stu-id="f2f7c-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2f7c-133">\<Element > Konfigurace</span><span class="sxs-lookup"><span data-stu-id="f2f7c-133">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="f2f7c-134">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|[<span data-ttu-id="f2f7c-135">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="f2f7c-135">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="f2f7c-136">Určuje nastavení konfigurace kompilátoru pro dostupné poskytovatele jazyků.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-136">Specifies compiler configuration settings for available language providers.</span></span>|
|[<span data-ttu-id="f2f7c-137">\<kompilátory > element</span><span class="sxs-lookup"><span data-stu-id="f2f7c-137">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="f2f7c-138">Kontejner pro prvky konfigurace kompilátoru; obsahuje nula nebo více `<compiler>` prvků.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-138">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f2f7c-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f2f7c-139">Remarks</span></span>

<span data-ttu-id="f2f7c-140">Každý `<compiler>` prvek určuje atributy konfigurace kompilátoru pro konkrétního poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-140">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="f2f7c-141">Zprostředkovatel rozšiřuje <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> třídu pro určitý jazyk `<compiler>` . element definuje kompilátor a nastavení generátoru kódu pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-141">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>

<span data-ttu-id="f2f7c-142">.NET Framework definuje počáteční nastavení kompilátoru v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="f2f7c-142">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="f2f7c-143">Vývojáři a dodavatelé kompilátoru můžou přidat konfigurační nastavení pro novou <xref:System.CodeDom.Compiler.CodeDomProvider> implementaci.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-143">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="f2f7c-144"><xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> Použijte metodu k programovému vytvoření výčtu poskytovatele jazyka a nastavení konfigurace kompilátoru v počítači.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-144">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>

<span data-ttu-id="f2f7c-145">Prvky kompilátoru v souboru aplikace nebo webové konfigurace mohou doplnit nebo přepsat nastavení v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-145">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="f2f7c-146">Pokud je pro stejný název jazyka nebo stejnou příponu souboru nakonfigurovaná víc než jedna implementace zprostředkovatele, přepíše poslední odpovídající konfigurace všechny předchozí nakonfigurované zprostředkovatele pro daný název jazyka nebo příponu souboru.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-146">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="f2f7c-147">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="f2f7c-147">Configuration File</span></span>

<span data-ttu-id="f2f7c-148">Tento element lze použít v konfiguračním souboru počítače a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f2f7c-148">This element can be used in the machine configuration file and the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="f2f7c-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2f7c-149">Example</span></span>

<span data-ttu-id="f2f7c-150">Následující příklad ilustruje typický prvek konfigurace kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="f2f7c-150">The following example illustrates a typical compiler configuration element:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f2f7c-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2f7c-151">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="f2f7c-152">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="f2f7c-152">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f2f7c-153">\<kompilátory > element</span><span class="sxs-lookup"><span data-stu-id="f2f7c-153">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="f2f7c-154">Určení úplných názvů typů</span><span class="sxs-lookup"><span data-stu-id="f2f7c-154">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="f2f7c-155">[Element Compiler pro kompilátory pro kompilaci (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f2f7c-155">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
