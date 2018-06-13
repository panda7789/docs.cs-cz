---
title: '&lt;System.CodeDom –&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5939fa31a2f87348922d4586e3e7b7b52066fb09
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744223"
---
# <a name="ltsystemcodedomgt-element"></a><span data-ttu-id="b0d59-102">&lt;System.CodeDom –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="b0d59-102">&lt;system.codedom&gt; Element</span></span>
<span data-ttu-id="b0d59-103">Určuje kompilátor – nastavení konfigurace pro zprostředkovatele dostupný jazyk.</span><span class="sxs-lookup"><span data-stu-id="b0d59-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
 <span data-ttu-id="b0d59-104">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="b0d59-104">\<configuration> Element</span></span>  
<span data-ttu-id="b0d59-105">\<System.CodeDom – > elementu</span><span class="sxs-lookup"><span data-stu-id="b0d59-105">\<system.codedom> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0d59-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0d59-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0d59-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b0d59-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b0d59-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b0d59-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0d59-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="b0d59-109">Attributes</span></span>  
 <span data-ttu-id="b0d59-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="b0d59-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b0d59-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b0d59-111">Child Elements</span></span>  
  
|<span data-ttu-id="b0d59-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="b0d59-112">Element</span></span>|<span data-ttu-id="b0d59-113">Popis</span><span class="sxs-lookup"><span data-stu-id="b0d59-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0d59-114">\<Kompilátory ></span><span class="sxs-lookup"><span data-stu-id="b0d59-114">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="b0d59-115">Kontejner pro kompilátor – elementy konfigurace; obsahuje nula nebo více [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="b0d59-115">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b0d59-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b0d59-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b0d59-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="b0d59-117">Element</span></span>|<span data-ttu-id="b0d59-118">Popis</span><span class="sxs-lookup"><span data-stu-id="b0d59-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0d59-119">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="b0d59-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="b0d59-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b0d59-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0d59-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b0d59-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="b0d59-122">Verze rozhraní .NET framework 2.0</span><span class="sxs-lookup"><span data-stu-id="b0d59-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="b0d59-123">[ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element obsahuje konfigurační nastavení kompilátoru pro jazyk poskytovatele nainstalovat do počítače kromě výchozí zprostředkovatele, které jsou nainstalovány s rozhraním .NET Framework, jako <xref:Microsoft.CSharp.CSharpCodeProvider> a <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="b0d59-123">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="b0d59-124">[ \<Kompilátory >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element obsahuje nula nebo více [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="b0d59-124">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="b0d59-125">Každý [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element určuje kompilátor – konfigurační atributy pro konkrétní jazyk zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="b0d59-125">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="b0d59-126">Vývojářům a dodavatelům kompilátoru můžete přidat nastavení konfigurace do konfiguračního souboru počítače (Machine.config) pro novou <xref:System.CodeDom.Compiler.CodeDomProvider> implementace.</span><span class="sxs-lookup"><span data-stu-id="b0d59-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="b0d59-127">Použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metoda prostřednictvím kódu programu výčet výchozí jazyk zprostředkovatele i zprostředkovatelé jazyka identifikovaný kompilátor – nastavení konfigurace v počítači.</span><span class="sxs-lookup"><span data-stu-id="b0d59-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0d59-128">V rozhraní .NET Framework verze 1.0 a 1.1, výchozí jazyk, se budou identifikovat poskytovatele dodané společností rozhraní .NET Framework [ \<kompilátory >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="b0d59-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element.</span></span> <span data-ttu-id="b0d59-129">V rozhraní .NET Framework verze 2.0, nejdou identifikovány výchozí jazyk zprostředkovatele v [ \<kompilátory >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elementu, ale mohou být uvedené pomocí <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="b0d59-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="b0d59-130">Rozhraní .NET framework verze 1.0 a 1.1</span><span class="sxs-lookup"><span data-stu-id="b0d59-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="b0d59-131">[ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element obsahuje konfigurační nastavení kompilátoru pro zprostředkovatelé jazyka v počítači.</span><span class="sxs-lookup"><span data-stu-id="b0d59-131">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="b0d59-132">[ \<Kompilátory >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element obsahuje nula nebo více [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="b0d59-132">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="b0d59-133">Každý [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element určuje kompilátor – konfigurační atributy pro konkrétní jazyk zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="b0d59-133">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="b0d59-134">Rozhraní .NET Framework definuje nastavení počáteční kompilátoru v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="b0d59-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="b0d59-135">Vývojářům a dodavatelům kompilátoru můžete přidat nastavení konfigurace pro novou <xref:System.CodeDom.Compiler.CodeDomProvider> implementace.</span><span class="sxs-lookup"><span data-stu-id="b0d59-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="b0d59-136">Použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metoda prostřednictvím kódu programu výčet zprostředkovatele a kompilátoru konfigurace nastavení jazyka v počítači.</span><span class="sxs-lookup"><span data-stu-id="b0d59-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="b0d59-137">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="b0d59-137">Configuration File</span></span>  
 <span data-ttu-id="b0d59-138">Tento element lze v konfiguračním souboru počítače a konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="b0d59-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0d59-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0d59-139">Example</span></span>  
 <span data-ttu-id="b0d59-140">Následující příklad znázorňuje konfiguraci typické kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="b0d59-140">The following example illustrates a typical compiler configuration.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler   
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=1.0.5000.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions=""  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0d59-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0d59-141">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="b0d59-142">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b0d59-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="b0d59-143">Schéma nastavení kompilátoru a poskytovatele jazyka</span><span class="sxs-lookup"><span data-stu-id="b0d59-143">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 [<span data-ttu-id="b0d59-144">\<kompilátoru > elementu</span><span class="sxs-lookup"><span data-stu-id="b0d59-144">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
