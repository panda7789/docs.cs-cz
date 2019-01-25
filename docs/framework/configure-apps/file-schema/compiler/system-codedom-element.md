---
title: '&lt;system.codedom&gt; Element'
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
ms.openlocfilehash: 235f3c2474acb488fecf34a64515973b45409e1b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649424"
---
# <a name="ltsystemcodedomgt-element"></a><span data-ttu-id="572a2-102">&lt;system.codedom&gt; Element</span><span class="sxs-lookup"><span data-stu-id="572a2-102">&lt;system.codedom&gt; Element</span></span>
<span data-ttu-id="572a2-103">Určuje konfigurační nastavení kompilátoru pro zprostředkovatele dostupných poskytovatelů jazyka.</span><span class="sxs-lookup"><span data-stu-id="572a2-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
 <span data-ttu-id="572a2-104">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="572a2-104">\<configuration> Element</span></span>  
<span data-ttu-id="572a2-105">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="572a2-105">\<system.codedom> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="572a2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="572a2-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="572a2-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="572a2-107">Attributes and Elements</span></span>  
 <span data-ttu-id="572a2-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="572a2-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="572a2-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="572a2-109">Attributes</span></span>  
 <span data-ttu-id="572a2-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="572a2-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="572a2-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="572a2-111">Child Elements</span></span>  
  
|<span data-ttu-id="572a2-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="572a2-112">Element</span></span>|<span data-ttu-id="572a2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="572a2-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="572a2-114">\<compilers></span><span class="sxs-lookup"><span data-stu-id="572a2-114">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="572a2-115">Kontejner pro kompilátor – elementy konfigurace; obsahuje nulu nebo více [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="572a2-115">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="572a2-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="572a2-116">Parent Elements</span></span>  
  
|<span data-ttu-id="572a2-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="572a2-117">Element</span></span>|<span data-ttu-id="572a2-118">Popis</span><span class="sxs-lookup"><span data-stu-id="572a2-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="572a2-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="572a2-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="572a2-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="572a2-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="572a2-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="572a2-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="572a2-122">Rozhraní .NET framework verze 2.0</span><span class="sxs-lookup"><span data-stu-id="572a2-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="572a2-123">[ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element obsahuje konfigurační nastavení kompilátoru pro poskytovatele jazyk nainstalovaný v počítači se kromě výchozího zprostředkovatele, které jsou nainstalovány s rozhraním .NET Framework, jako <xref:Microsoft.CSharp.CSharpCodeProvider> a <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="572a2-123">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="572a2-124">[ \<Compilers >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) prvek obsahuje nula nebo více [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="572a2-124">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="572a2-125">Každý [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) prvek určuje kompilátor – konfigurační atributy pro konkrétní jazyk zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="572a2-125">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="572a2-126">Vývojářům a dodavatelům kompilátoru můžete přidat konfigurační nastavení do konfiguračního souboru počítače (Machine.config) pro nový <xref:System.CodeDom.Compiler.CodeDomProvider> implementace.</span><span class="sxs-lookup"><span data-stu-id="572a2-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="572a2-127">Použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metoda jak programově vytvářet výčty výchozí jazyk poskytovatele i zprostředkovatelé jazyka identifikovaný kompilátor – nastavení konfigurace v počítači.</span><span class="sxs-lookup"><span data-stu-id="572a2-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="572a2-128">V rozhraní .NET Framework verze 1.0 a 1.1, výchozí jazyk poskytovatele dodané rozhraním .NET Framework jsou uvedené v [ \<compilers >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="572a2-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element.</span></span> <span data-ttu-id="572a2-129">V rozhraní .NET Framework verze 2.0, výchozí jazyk poskytovatele nejsou uvedené v [ \<kompilátory >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elementu, ale mohou být uvedené použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="572a2-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="572a2-130">Rozhraní .NET framework verze 1.0 a 1.1</span><span class="sxs-lookup"><span data-stu-id="572a2-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="572a2-131">[ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element obsahuje konfigurační nastavení kompilátoru pro poskytovatele jazyka v počítači.</span><span class="sxs-lookup"><span data-stu-id="572a2-131">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="572a2-132">[ \<Compilers >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) prvek obsahuje nula nebo více [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="572a2-132">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="572a2-133">Každý [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) prvek určuje kompilátor – konfigurační atributy pro konkrétní jazyk zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="572a2-133">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="572a2-134">Rozhraní .NET Framework definuje počáteční kompilátor – nastavení v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="572a2-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="572a2-135">Vývojářům a dodavatelům kompilátoru můžete přidat nastavení konfigurace pro nové <xref:System.CodeDom.Compiler.CodeDomProvider> implementace.</span><span class="sxs-lookup"><span data-stu-id="572a2-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="572a2-136">Použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> způsob, jak programově vytvářet výčty zprostředkovatele a kompilátoru konfigurace nastavení jazyka v počítači.</span><span class="sxs-lookup"><span data-stu-id="572a2-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="572a2-137">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="572a2-137">Configuration File</span></span>  
 <span data-ttu-id="572a2-138">Tento element lze použít v konfiguračním souboru počítače a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="572a2-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="572a2-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="572a2-139">Example</span></span>  
 <span data-ttu-id="572a2-140">Následující příklad ukazuje typické kompilátoru konfigurace.</span><span class="sxs-lookup"><span data-stu-id="572a2-140">The following example illustrates a typical compiler configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="572a2-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="572a2-141">See also</span></span>
- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="572a2-142">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="572a2-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="572a2-143">Schéma nastavení kompilátoru a poskytovatele jazyka</span><span class="sxs-lookup"><span data-stu-id="572a2-143">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)
- [<span data-ttu-id="572a2-144">\<Kompilátor > – Element</span><span class="sxs-lookup"><span data-stu-id="572a2-144">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
