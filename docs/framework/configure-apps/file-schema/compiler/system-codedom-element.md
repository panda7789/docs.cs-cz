---
title: <system.codedom> – element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
ms.openlocfilehash: 40a3c84e1deed4d215383670176623a6a79ac41d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155385"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="f107b-102">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="f107b-102">\<system.codedom> Element</span></span>
<span data-ttu-id="f107b-103">Určuje nastavení konfigurace kompilátoru pro dostupné poskytovatele jazyků.</span><span class="sxs-lookup"><span data-stu-id="f107b-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
[<span data-ttu-id="f107b-104">**\<>konfigurace**</span><span class="sxs-lookup"><span data-stu-id="f107b-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="f107b-105">&nbsp;&nbsp;**\<system.codedom>**</span><span class="sxs-lookup"><span data-stu-id="f107b-105">&nbsp;&nbsp;**\<system.codedom>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f107b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f107b-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f107b-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f107b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f107b-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f107b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f107b-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="f107b-109">Attributes</span></span>  
 <span data-ttu-id="f107b-110">Žádné.</span><span class="sxs-lookup"><span data-stu-id="f107b-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f107b-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f107b-111">Child Elements</span></span>  
  
|<span data-ttu-id="f107b-112">Element</span><span class="sxs-lookup"><span data-stu-id="f107b-112">Element</span></span>|<span data-ttu-id="f107b-113">Popis</span><span class="sxs-lookup"><span data-stu-id="f107b-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f107b-114">\<>kompilátorů</span><span class="sxs-lookup"><span data-stu-id="f107b-114">\<compilers></span></span>](compilers-element.md)|<span data-ttu-id="f107b-115">Kontejner pro konfigurační prvky kompilátoru; obsahuje nula [ \<](compiler-element.md) nebo více>prvků kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f107b-115">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f107b-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f107b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="f107b-117">Element</span><span class="sxs-lookup"><span data-stu-id="f107b-117">Element</span></span>|<span data-ttu-id="f107b-118">Popis</span><span class="sxs-lookup"><span data-stu-id="f107b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f107b-119">\<>konfigurace</span><span class="sxs-lookup"><span data-stu-id="f107b-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="f107b-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f107b-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f107b-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f107b-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="f107b-122">Rozhraní .NET Framework verze 2.0</span><span class="sxs-lookup"><span data-stu-id="f107b-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="f107b-123">Element [ \<system.codedom>](system-codedom-element.md) obsahuje nastavení konfigurace kompilátoru pro poskytovatele jazyků nainstalovaných v počítači kromě výchozích <xref:Microsoft.VisualBasic.VBCodeProvider>zprostředkovatelů nainstalovaných pomocí rozhraní .NET Framework, například <xref:Microsoft.CSharp.CSharpCodeProvider> rozhraní a .</span><span class="sxs-lookup"><span data-stu-id="f107b-123">The [\<system.codedom>](system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="f107b-124">[ \<Kompilátory>](compilers-element.md) element obsahuje nula nebo více [ \<>prvků kompilátoru.](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="f107b-124">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="f107b-125">Každý [ \<prvek>kompilátoru](compiler-element.md) určuje atributy konfigurace kompilátoru pro konkrétního poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="f107b-125">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="f107b-126">Vývojáři a dodavatelé kompilátoru mohou přidat nastavení konfigurace do konfiguračního souboru počítače (Machine.config) pro novou <xref:System.CodeDom.Compiler.CodeDomProvider> implementaci.</span><span class="sxs-lookup"><span data-stu-id="f107b-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="f107b-127">Pomocí <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> této metody můžete programově vytvořit výčet výchozích poskytovatelů jazyků a poskytovatelů jazyků identifikovaných nastavením konfigurace kompilátoru v počítači.</span><span class="sxs-lookup"><span data-stu-id="f107b-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f107b-128">V rozhraní .NET Framework verze 1.0 a 1.1 jsou v [ \<kompilátorech>](compilers-element.md) elementu identifikováni výchozí poskytovatelé jazyků dodaná rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f107b-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](compilers-element.md) element.</span></span> <span data-ttu-id="f107b-129">V rozhraní .NET Framework verze 2.0 nejsou výchozí poskytovatelé jazyka identifikováni v [ \<kompilátorech>](compilers-element.md) elementu, ale lze je vyjmenovat pomocí <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f107b-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="f107b-130">Rozhraní .NET Framework verze 1.0 a 1.1</span><span class="sxs-lookup"><span data-stu-id="f107b-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="f107b-131">Element [ \<system.codedom>](system-codedom-element.md) obsahuje nastavení konfigurace kompilátoru pro poskytovatele jazyků v počítači.</span><span class="sxs-lookup"><span data-stu-id="f107b-131">The [\<system.codedom>](system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="f107b-132">[ \<Kompilátory>](compilers-element.md) element obsahuje nula nebo více [ \<>prvků kompilátoru.](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="f107b-132">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="f107b-133">Každý [ \<prvek>kompilátoru](compiler-element.md) určuje atributy konfigurace kompilátoru pro konkrétního poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="f107b-133">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="f107b-134">Rozhraní .NET Framework definuje počáteční nastavení kompilátoru v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="f107b-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="f107b-135">Vývojáři a dodavatelé kompilátoru <xref:System.CodeDom.Compiler.CodeDomProvider> mohou přidat nastavení konfigurace pro novou implementaci.</span><span class="sxs-lookup"><span data-stu-id="f107b-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="f107b-136">Pomocí <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> této metody můžete programově vytvořit výčet nastavení poskytovatele jazyka a konfigurace kompilátoru v počítači.</span><span class="sxs-lookup"><span data-stu-id="f107b-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="f107b-137">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="f107b-137">Configuration File</span></span>  
 <span data-ttu-id="f107b-138">Tento prvek lze použít v konfiguračním souboru počítače a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f107b-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f107b-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="f107b-139">Example</span></span>  
 <span data-ttu-id="f107b-140">Následující příklad ilustruje typickou konfiguraci kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f107b-140">The following example illustrates a typical compiler configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f107b-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="f107b-141">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="f107b-142">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="f107b-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f107b-143">Schéma nastavení kompilátoru a poskytovatele jazyka</span><span class="sxs-lookup"><span data-stu-id="f107b-143">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f107b-144">\<> element kompilátoru</span><span class="sxs-lookup"><span data-stu-id="f107b-144">\<compiler> Element</span></span>](compiler-element.md)
