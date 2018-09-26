---
title: '&lt;System.CodeDom&gt; – Element'
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
ms.openlocfilehash: ea9fd06887c9a4bc9f121945f27753dfc666cfec
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47078386"
---
# <a name="ltsystemcodedomgt-element"></a><span data-ttu-id="5b62e-102">&lt;System.CodeDom&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="5b62e-102">&lt;system.codedom&gt; Element</span></span>
<span data-ttu-id="5b62e-103">Určuje konfigurační nastavení kompilátoru pro zprostředkovatele dostupných poskytovatelů jazyka.</span><span class="sxs-lookup"><span data-stu-id="5b62e-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
 <span data-ttu-id="5b62e-104">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="5b62e-104">\<configuration> Element</span></span>  
<span data-ttu-id="5b62e-105">\<System.CodeDom > – Element</span><span class="sxs-lookup"><span data-stu-id="5b62e-105">\<system.codedom> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b62e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b62e-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b62e-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5b62e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="5b62e-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5b62e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b62e-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="5b62e-109">Attributes</span></span>  
 <span data-ttu-id="5b62e-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="5b62e-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5b62e-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5b62e-111">Child Elements</span></span>  
  
|<span data-ttu-id="5b62e-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="5b62e-112">Element</span></span>|<span data-ttu-id="5b62e-113">Popis</span><span class="sxs-lookup"><span data-stu-id="5b62e-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b62e-114">\<Kompilátory ></span><span class="sxs-lookup"><span data-stu-id="5b62e-114">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="5b62e-115">Kontejner pro kompilátor – elementy konfigurace; obsahuje nulu nebo více [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="5b62e-115">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5b62e-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5b62e-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5b62e-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="5b62e-117">Element</span></span>|<span data-ttu-id="5b62e-118">Popis</span><span class="sxs-lookup"><span data-stu-id="5b62e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b62e-119">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="5b62e-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="5b62e-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5b62e-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b62e-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b62e-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="5b62e-122">Rozhraní .NET framework verze 2.0</span><span class="sxs-lookup"><span data-stu-id="5b62e-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="5b62e-123">[ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element obsahuje konfigurační nastavení kompilátoru pro poskytovatele jazyk nainstalovaný v počítači se kromě výchozího zprostředkovatele, které jsou nainstalovány s rozhraním .NET Framework, jako <xref:Microsoft.CSharp.CSharpCodeProvider> a <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="5b62e-123">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="5b62e-124">[ \<Compilers >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) prvek obsahuje nula nebo více [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="5b62e-124">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="5b62e-125">Každý [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) prvek určuje kompilátor – konfigurační atributy pro konkrétní jazyk zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="5b62e-125">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="5b62e-126">Vývojářům a dodavatelům kompilátoru můžete přidat konfigurační nastavení do konfiguračního souboru počítače (Machine.config) pro nový <xref:System.CodeDom.Compiler.CodeDomProvider> implementace.</span><span class="sxs-lookup"><span data-stu-id="5b62e-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="5b62e-127">Použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metoda jak programově vytvářet výčty výchozí jazyk poskytovatele i zprostředkovatelé jazyka identifikovaný kompilátor – nastavení konfigurace v počítači.</span><span class="sxs-lookup"><span data-stu-id="5b62e-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b62e-128">V rozhraní .NET Framework verze 1.0 a 1.1, výchozí jazyk poskytovatele dodané rozhraním .NET Framework jsou uvedené v [ \<compilers >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="5b62e-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element.</span></span> <span data-ttu-id="5b62e-129">V rozhraní .NET Framework verze 2.0, výchozí jazyk poskytovatele nejsou uvedené v [ \<kompilátory >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elementu, ale mohou být uvedené použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5b62e-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="5b62e-130">Rozhraní .NET framework verze 1.0 a 1.1</span><span class="sxs-lookup"><span data-stu-id="5b62e-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="5b62e-131">[ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element obsahuje konfigurační nastavení kompilátoru pro poskytovatele jazyka v počítači.</span><span class="sxs-lookup"><span data-stu-id="5b62e-131">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="5b62e-132">[ \<Compilers >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) prvek obsahuje nula nebo více [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="5b62e-132">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="5b62e-133">Každý [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) prvek určuje kompilátor – konfigurační atributy pro konkrétní jazyk zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="5b62e-133">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="5b62e-134">Rozhraní .NET Framework definuje počáteční kompilátor – nastavení v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="5b62e-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="5b62e-135">Vývojářům a dodavatelům kompilátoru můžete přidat nastavení konfigurace pro nové <xref:System.CodeDom.Compiler.CodeDomProvider> implementace.</span><span class="sxs-lookup"><span data-stu-id="5b62e-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="5b62e-136">Použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> způsob, jak programově vytvářet výčty zprostředkovatele a kompilátoru konfigurace nastavení jazyka v počítači.</span><span class="sxs-lookup"><span data-stu-id="5b62e-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="5b62e-137">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="5b62e-137">Configuration File</span></span>  
 <span data-ttu-id="5b62e-138">Tento element lze použít v konfiguračním souboru počítače a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="5b62e-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b62e-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="5b62e-139">Example</span></span>  
 <span data-ttu-id="5b62e-140">Následující příklad ukazuje typické kompilátoru konfigurace.</span><span class="sxs-lookup"><span data-stu-id="5b62e-140">The following example illustrates a typical compiler configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5b62e-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b62e-141">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="5b62e-142">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="5b62e-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="5b62e-143">Schéma nastavení kompilátoru a poskytovatele jazyka</span><span class="sxs-lookup"><span data-stu-id="5b62e-143">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 [<span data-ttu-id="5b62e-144">\<Kompilátor > – Element</span><span class="sxs-lookup"><span data-stu-id="5b62e-144">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
