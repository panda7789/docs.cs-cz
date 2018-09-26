---
title: '&lt;Kompilátor&gt; – Element'
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: a26fc0bda341e85ca54f3dee4addd14e4164209c
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193954"
---
# <a name="ltcompilergt-element"></a><span data-ttu-id="9748e-102">&lt;Kompilátor&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="9748e-102">&lt;compiler&gt; Element</span></span>

<span data-ttu-id="9748e-103">Určuje kompilátor – konfigurační atributy pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="9748e-103">Specifies the compiler configuration attributes for a language provider.</span></span>

<span data-ttu-id="9748e-104">\<Konfigurace Element > \<System.CodeDom – Element > \<kompilátory Element > \<kompilátoru > – Element</span><span class="sxs-lookup"><span data-stu-id="9748e-104">\<configuration Element> \<system.codedom Element> \<compilers Element> \<compiler> Element</span></span>

## <a name="syntax"></a><span data-ttu-id="9748e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9748e-105">Syntax</span></span>

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9748e-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9748e-106">Attributes and Elements</span></span>

<span data-ttu-id="9748e-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9748e-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9748e-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="9748e-108">Attributes</span></span>

|<span data-ttu-id="9748e-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="9748e-109">Attribute</span></span>|<span data-ttu-id="9748e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="9748e-110">Description</span></span>|
|---------------|-----------------|
|`compilerOptions`|<span data-ttu-id="9748e-111">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="9748e-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="9748e-112">Určuje další argumenty kompilátoru specifické pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="9748e-112">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="9748e-113">Hodnoty `compilerOptions` atribut jsou obvykle uvedeny v tématu možnosti kompilátoru pro kompilátor.</span><span class="sxs-lookup"><span data-stu-id="9748e-113">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span>|
|`extension`|<span data-ttu-id="9748e-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="9748e-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="9748e-115">Poskytuje středníkem oddělený seznam přípon názvů souborů používá zdrojové soubory pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="9748e-115">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="9748e-116">Například "cs".</span><span class="sxs-lookup"><span data-stu-id="9748e-116">For example, ".cs".</span></span>|
|`language`|<span data-ttu-id="9748e-117">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="9748e-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="9748e-118">Poskytuje středníkem oddělený seznam názvů jazyka podporována zprostředkovatelem jazyka.</span><span class="sxs-lookup"><span data-stu-id="9748e-118">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="9748e-119">Například "c#; cs; csharp".</span><span class="sxs-lookup"><span data-stu-id="9748e-119">For example, "c#;cs;csharp".</span></span>|
|`type`|<span data-ttu-id="9748e-120">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="9748e-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="9748e-121">Určuje název typu poskytovatele jazyka, včetně název sestavení obsahujícího implementaci zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="9748e-121">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="9748e-122">Název typu, musí splňovat požadavky definované v [zadání plně kvalifikované názvy typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="9748e-122">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|
|`warningLevel`|<span data-ttu-id="9748e-123">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="9748e-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="9748e-124">Určuje výchozí úroveň upozornění kompilátoru; Určuje úroveň, kdy zprostředkovatel jazyka zpracuje kompilace upozornění jako chyby.</span><span class="sxs-lookup"><span data-stu-id="9748e-124">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="9748e-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9748e-125">Child Elements</span></span>

|<span data-ttu-id="9748e-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="9748e-126">Element</span></span>|<span data-ttu-id="9748e-127">Popis</span><span class="sxs-lookup"><span data-stu-id="9748e-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9748e-128">\<provideroption – > – Element</span><span class="sxs-lookup"><span data-stu-id="9748e-128">\<providerOption> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|<span data-ttu-id="9748e-129">Určuje atributy verze kompilátoru poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="9748e-129">Specifies compiler version attributes for a language provider.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9748e-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9748e-130">Parent Elements</span></span>

|<span data-ttu-id="9748e-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="9748e-131">Element</span></span>|<span data-ttu-id="9748e-132">Popis</span><span class="sxs-lookup"><span data-stu-id="9748e-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9748e-133">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="9748e-133">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="9748e-134">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9748e-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|[<span data-ttu-id="9748e-135">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="9748e-135">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="9748e-136">Určuje konfigurační nastavení kompilátoru pro zprostředkovatele dostupných poskytovatelů jazyka.</span><span class="sxs-lookup"><span data-stu-id="9748e-136">Specifies compiler configuration settings for available language providers.</span></span>|
|[<span data-ttu-id="9748e-137">\<Kompilátory > – Element</span><span class="sxs-lookup"><span data-stu-id="9748e-137">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="9748e-138">Kontejner pro kompilátor – elementy konfigurace; obsahuje nulu nebo více `<compiler>` elementy.</span><span class="sxs-lookup"><span data-stu-id="9748e-138">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9748e-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9748e-139">Remarks</span></span>

<span data-ttu-id="9748e-140">Každý `<compiler>` prvek určuje kompilátor – konfigurační atributy pro konkrétní jazyk zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="9748e-140">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="9748e-141">Zprostředkovatel rozšiřuje <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> třídy pro konkrétní jazyk; `<compiler>` element definuje kompilátoru a nastavení generátor kódu pro jazyk zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="9748e-141">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>

<span data-ttu-id="9748e-142">Rozhraní .NET Framework definuje počáteční kompilátor – nastavení v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="9748e-142">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="9748e-143">Vývojářům a dodavatelům kompilátoru můžete přidat nastavení konfigurace pro nové <xref:System.CodeDom.Compiler.CodeDomProvider> implementace.</span><span class="sxs-lookup"><span data-stu-id="9748e-143">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="9748e-144">Použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> způsob, jak programově vytvářet výčty zprostředkovatele a kompilátoru konfigurace nastavení jazyka v počítači.</span><span class="sxs-lookup"><span data-stu-id="9748e-144">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>

<span data-ttu-id="9748e-145">Kompilátor elementy v adresáři aplikace nebo souboru konfigurace webu můžete doplnit nebo přepsat nastavení v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="9748e-145">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="9748e-146">Pokud více než jednu implementaci zprostředkovatele je nakonfigurovaný pro stejný název jazyka nebo stejnou příponu, poslední odpovídající konfigurace přepíše jakékoli předchozí nakonfigurované zprostředkovatelé pro tento jazyk název nebo příponu souboru.</span><span class="sxs-lookup"><span data-stu-id="9748e-146">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="9748e-147">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="9748e-147">Configuration File</span></span>

<span data-ttu-id="9748e-148">Tento element lze použít v konfiguračním souboru počítače a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="9748e-148">This element can be used in the machine configuration file and the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="9748e-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="9748e-149">Example</span></span>

<span data-ttu-id="9748e-150">Následující příklad ukazuje prvek typické kompilátoru konfigurace:</span><span class="sxs-lookup"><span data-stu-id="9748e-150">The following example illustrates a typical compiler configuration element:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9748e-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="9748e-151">See Also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="9748e-152">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="9748e-152">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="9748e-153">\<Kompilátory > – Element</span><span class="sxs-lookup"><span data-stu-id="9748e-153">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)
- <span data-ttu-id="9748e-154">[Zadání plně kvalifikované názvy typů]-(.. /.. /.. /.. /.. / docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)</span><span class="sxs-lookup"><span data-stu-id="9748e-154">[Specifying Fully Qualified Type Names]-(../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)</span></span>
- <span data-ttu-id="9748e-155">[Kompilátor – Element pro kompilátory compilation (schéma nastavení technologie ASP.NET)](https://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9748e-155">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e(v=vs.100))</span></span>
