---
title: <system.codedom> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
ms.openlocfilehash: 0f47255bb4073007a847e4a8b85ccfd34100582b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101611"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="3b824-102">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="3b824-102">\<system.codedom> Element</span></span>
<span data-ttu-id="3b824-103">Určuje konfigurační nastavení kompilátoru pro zprostředkovatele dostupných poskytovatelů jazyka.</span><span class="sxs-lookup"><span data-stu-id="3b824-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
 <span data-ttu-id="3b824-104">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="3b824-104">\<configuration> Element</span></span>  
<span data-ttu-id="3b824-105">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="3b824-105">\<system.codedom> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b824-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b824-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b824-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3b824-107">Attributes and Elements</span></span>  
 <span data-ttu-id="3b824-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3b824-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b824-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="3b824-109">Attributes</span></span>  
 <span data-ttu-id="3b824-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="3b824-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3b824-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3b824-111">Child Elements</span></span>  
  
|<span data-ttu-id="3b824-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="3b824-112">Element</span></span>|<span data-ttu-id="3b824-113">Popis</span><span class="sxs-lookup"><span data-stu-id="3b824-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3b824-114">\<compilers></span><span class="sxs-lookup"><span data-stu-id="3b824-114">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="3b824-115">Kontejner pro kompilátor – elementy konfigurace; obsahuje nulu nebo více [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="3b824-115">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3b824-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3b824-116">Parent Elements</span></span>  
  
|<span data-ttu-id="3b824-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="3b824-117">Element</span></span>|<span data-ttu-id="3b824-118">Popis</span><span class="sxs-lookup"><span data-stu-id="3b824-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3b824-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="3b824-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="3b824-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3b824-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b824-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3b824-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="3b824-122">Rozhraní .NET framework verze 2.0</span><span class="sxs-lookup"><span data-stu-id="3b824-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="3b824-123">[ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element obsahuje konfigurační nastavení kompilátoru pro poskytovatele jazyk nainstalovaný v počítači se kromě výchozího zprostředkovatele, které jsou nainstalovány s rozhraním .NET Framework, jako <xref:Microsoft.CSharp.CSharpCodeProvider> a <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="3b824-123">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="3b824-124">[ \<Compilers >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) prvek obsahuje nula nebo více [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="3b824-124">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="3b824-125">Každý [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) prvek určuje kompilátor – konfigurační atributy pro konkrétní jazyk zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="3b824-125">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="3b824-126">Vývojářům a dodavatelům kompilátoru můžete přidat konfigurační nastavení do konfiguračního souboru počítače (Machine.config) pro nový <xref:System.CodeDom.Compiler.CodeDomProvider> implementace.</span><span class="sxs-lookup"><span data-stu-id="3b824-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="3b824-127">Použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metoda jak programově vytvářet výčty výchozí jazyk poskytovatele i zprostředkovatelé jazyka identifikovaný kompilátor – nastavení konfigurace v počítači.</span><span class="sxs-lookup"><span data-stu-id="3b824-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b824-128">V rozhraní .NET Framework verze 1.0 a 1.1, výchozí jazyk poskytovatele dodané rozhraním .NET Framework jsou uvedené v [ \<compilers >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="3b824-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element.</span></span> <span data-ttu-id="3b824-129">V rozhraní .NET Framework verze 2.0, výchozí jazyk poskytovatele nejsou uvedené v [ \<kompilátory >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elementu, ale mohou být uvedené použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3b824-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="3b824-130">Rozhraní .NET framework verze 1.0 a 1.1</span><span class="sxs-lookup"><span data-stu-id="3b824-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="3b824-131">[ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element obsahuje konfigurační nastavení kompilátoru pro poskytovatele jazyka v počítači.</span><span class="sxs-lookup"><span data-stu-id="3b824-131">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="3b824-132">[ \<Compilers >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) prvek obsahuje nula nebo více [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="3b824-132">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="3b824-133">Každý [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) prvek určuje kompilátor – konfigurační atributy pro konkrétní jazyk zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="3b824-133">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="3b824-134">Rozhraní .NET Framework definuje počáteční kompilátor – nastavení v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="3b824-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="3b824-135">Vývojářům a dodavatelům kompilátoru můžete přidat nastavení konfigurace pro nové <xref:System.CodeDom.Compiler.CodeDomProvider> implementace.</span><span class="sxs-lookup"><span data-stu-id="3b824-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="3b824-136">Použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> způsob, jak programově vytvářet výčty zprostředkovatele a kompilátoru konfigurace nastavení jazyka v počítači.</span><span class="sxs-lookup"><span data-stu-id="3b824-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="3b824-137">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="3b824-137">Configuration File</span></span>  
 <span data-ttu-id="3b824-138">Tento element lze použít v konfiguračním souboru počítače a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="3b824-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b824-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b824-139">Example</span></span>  
 <span data-ttu-id="3b824-140">Následující příklad ukazuje typické kompilátoru konfigurace.</span><span class="sxs-lookup"><span data-stu-id="3b824-140">The following example illustrates a typical compiler configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3b824-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b824-141">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="3b824-142">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="3b824-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="3b824-143">Schéma nastavení kompilátoru a poskytovatele jazyka</span><span class="sxs-lookup"><span data-stu-id="3b824-143">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)
- [<span data-ttu-id="3b824-144">\<Kompilátor > – Element</span><span class="sxs-lookup"><span data-stu-id="3b824-144">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
