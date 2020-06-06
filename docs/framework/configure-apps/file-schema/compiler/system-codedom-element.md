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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155385"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="43e00-102">Element \<system.codedom></span><span class="sxs-lookup"><span data-stu-id="43e00-102">\<system.codedom> Element</span></span>
<span data-ttu-id="43e00-103">Určuje nastavení konfigurace kompilátoru pro dostupné poskytovatele jazyků.</span><span class="sxs-lookup"><span data-stu-id="43e00-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.codedom>**  
  
## <a name="syntax"></a><span data-ttu-id="43e00-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43e00-104">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43e00-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="43e00-105">Attributes and Elements</span></span>  
 <span data-ttu-id="43e00-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="43e00-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43e00-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="43e00-107">Attributes</span></span>  
 <span data-ttu-id="43e00-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="43e00-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="43e00-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="43e00-109">Child Elements</span></span>  
  
|<span data-ttu-id="43e00-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="43e00-110">Element</span></span>|<span data-ttu-id="43e00-111">Description</span><span class="sxs-lookup"><span data-stu-id="43e00-111">Description</span></span>|  
|-------------|-----------------|  
|[\<compilers>](compilers-element.md)|<span data-ttu-id="43e00-112">Kontejner pro prvky konfigurace kompilátoru; obsahuje nula nebo více [\<compiler>](compiler-element.md) prvků.</span><span class="sxs-lookup"><span data-stu-id="43e00-112">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="43e00-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="43e00-113">Parent Elements</span></span>  
  
|<span data-ttu-id="43e00-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="43e00-114">Element</span></span>|<span data-ttu-id="43e00-115">Description</span><span class="sxs-lookup"><span data-stu-id="43e00-115">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="43e00-116">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="43e00-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43e00-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43e00-117">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="43e00-118">.NET Framework verze 2,0</span><span class="sxs-lookup"><span data-stu-id="43e00-118">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="43e00-119">[\<system.codedom>](system-codedom-element.md)Element obsahuje nastavení konfigurace kompilátoru pro jazykové zprostředkovatele nainstalované v počítači kromě výchozích zprostředkovatelů, které jsou nainstalovány s .NET Framework, jako jsou <xref:Microsoft.CSharp.CSharpCodeProvider> a <xref:Microsoft.VisualBasic.VBCodeProvider> .</span><span class="sxs-lookup"><span data-stu-id="43e00-119">The [\<system.codedom>](system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="43e00-120">[\<compilers>](compilers-element.md)Element obsahuje nula nebo více [\<compiler>](compiler-element.md) prvků.</span><span class="sxs-lookup"><span data-stu-id="43e00-120">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="43e00-121">Každý [\<compiler>](compiler-element.md) prvek určuje atributy konfigurace kompilátoru pro konkrétního poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="43e00-121">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="43e00-122">Vývojáři a dodavatelé kompilátoru můžou přidat konfigurační nastavení do konfiguračního souboru počítače (Machine. config) pro novou <xref:System.CodeDom.Compiler.CodeDomProvider> implementaci.</span><span class="sxs-lookup"><span data-stu-id="43e00-122">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="43e00-123">Použijte <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metodu pro programové vytvoření výčtu výchozích zprostředkovatelů jazyků a poskytovatelů jazyka identifikovaných nastavením konfigurace kompilátoru v počítači.</span><span class="sxs-lookup"><span data-stu-id="43e00-123">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="43e00-124">V .NET Framework verzích 1,0 a 1,1 jsou v elementu identifikováni výchozí poskytovatelé jazyka poskytnuté .NET Framework [\<compilers>](compilers-element.md) .</span><span class="sxs-lookup"><span data-stu-id="43e00-124">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](compilers-element.md) element.</span></span> <span data-ttu-id="43e00-125">V .NET Framework verze 2,0 nejsou v elementu identifikováni výchozí poskytovatelé jazyka [\<compilers>](compilers-element.md) , ale lze je vyčíslit pomocí <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="43e00-125">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="43e00-126">.NET Framework verze 1,0 a 1,1</span><span class="sxs-lookup"><span data-stu-id="43e00-126">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="43e00-127">[\<system.codedom>](system-codedom-element.md)Element obsahuje nastavení konfigurace kompilátoru pro poskytovatele jazyků v počítači.</span><span class="sxs-lookup"><span data-stu-id="43e00-127">The [\<system.codedom>](system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="43e00-128">[\<compilers>](compilers-element.md)Element obsahuje nula nebo více [\<compiler>](compiler-element.md) prvků.</span><span class="sxs-lookup"><span data-stu-id="43e00-128">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="43e00-129">Každý [\<compiler>](compiler-element.md) prvek určuje atributy konfigurace kompilátoru pro konkrétního poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="43e00-129">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="43e00-130">.NET Framework definuje počáteční nastavení kompilátoru v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="43e00-130">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="43e00-131">Vývojáři a dodavatelé kompilátoru můžou přidat konfigurační nastavení pro novou <xref:System.CodeDom.Compiler.CodeDomProvider> implementaci.</span><span class="sxs-lookup"><span data-stu-id="43e00-131">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="43e00-132">Použijte <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metodu k programovému vytvoření výčtu poskytovatele jazyka a nastavení konfigurace kompilátoru v počítači.</span><span class="sxs-lookup"><span data-stu-id="43e00-132">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="43e00-133">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="43e00-133">Configuration File</span></span>  
 <span data-ttu-id="43e00-134">Tento element lze použít v konfiguračním souboru počítače a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="43e00-134">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43e00-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="43e00-135">Example</span></span>  
 <span data-ttu-id="43e00-136">Následující příklad ilustruje typickou konfiguraci kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="43e00-136">The following example illustrates a typical compiler configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43e00-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="43e00-137">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="43e00-138">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="43e00-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="43e00-139">Schéma nastavení kompilátoru a poskytovatele jazyka</span><span class="sxs-lookup"><span data-stu-id="43e00-139">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="43e00-140">\<compiler>Objekt</span><span class="sxs-lookup"><span data-stu-id="43e00-140">\<compiler> Element</span></span>](compiler-element.md)
