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
ms.openlocfilehash: 43bc3c40bfc0b0ce4c0b18683092faf8b67e1c04
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927697"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="ab24a-102">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="ab24a-102">\<system.codedom> Element</span></span>
<span data-ttu-id="ab24a-103">Určuje nastavení konfigurace kompilátoru pro dostupné poskytovatele jazyků.</span><span class="sxs-lookup"><span data-stu-id="ab24a-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
 <span data-ttu-id="ab24a-104">\<Element > Konfigurace</span><span class="sxs-lookup"><span data-stu-id="ab24a-104">\<configuration> Element</span></span>  
<span data-ttu-id="ab24a-105">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="ab24a-105">\<system.codedom> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab24a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab24a-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab24a-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ab24a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="ab24a-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ab24a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab24a-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="ab24a-109">Attributes</span></span>  
 <span data-ttu-id="ab24a-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="ab24a-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ab24a-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ab24a-111">Child Elements</span></span>  
  
|<span data-ttu-id="ab24a-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="ab24a-112">Element</span></span>|<span data-ttu-id="ab24a-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ab24a-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab24a-114">\<compilers></span><span class="sxs-lookup"><span data-stu-id="ab24a-114">\<compilers></span></span>](compilers-element.md)|<span data-ttu-id="ab24a-115">Kontejner pro prvky konfigurace kompilátoru; obsahuje nula nebo více [ \<elementů > kompilátoru](compiler-element.md) .</span><span class="sxs-lookup"><span data-stu-id="ab24a-115">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ab24a-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ab24a-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ab24a-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="ab24a-117">Element</span></span>|<span data-ttu-id="ab24a-118">Popis</span><span class="sxs-lookup"><span data-stu-id="ab24a-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab24a-119">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="ab24a-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="ab24a-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ab24a-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab24a-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab24a-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="ab24a-122">.NET Framework verze 2,0</span><span class="sxs-lookup"><span data-stu-id="ab24a-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="ab24a-123"><xref:Microsoft.CSharp.CSharpCodeProvider> [ ElementSystem.CodeDom>obsahujenastaveníkonfiguracekompilátoruprojazykovézprostředkovatelenainstalovanévpočítačikroměvýchozíchzprostředkovatelů,kteříjsounainstalováni\<](system-codedom-element.md) s .NET Framework, například a <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="ab24a-123">The [\<system.codedom>](system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="ab24a-124">Kompilátory > element obsahuje nula nebo více [ \<elementů > kompilátoru](compiler-element.md) . [ \<](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="ab24a-124">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="ab24a-125">[ Každý\<kompilátor >](compiler-element.md) element určuje atributy konfigurace kompilátoru pro konkrétního poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="ab24a-125">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="ab24a-126">Vývojáři a dodavatelé kompilátoru můžou přidat konfigurační nastavení do konfiguračního souboru počítače (Machine. config) pro novou <xref:System.CodeDom.Compiler.CodeDomProvider> implementaci.</span><span class="sxs-lookup"><span data-stu-id="ab24a-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="ab24a-127"><xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> Použijte metodu pro programové vytvoření výčtu výchozích zprostředkovatelů jazyků a poskytovatelů jazyka identifikovaných nastavením konfigurace kompilátoru v počítači.</span><span class="sxs-lookup"><span data-stu-id="ab24a-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab24a-128">Ve verzích .NET Framework 1,0 a 1,1 jsou výchozí poskytovatelé jazyka dodané .NET Framework identifikováni v [ \<prvku > kompilátoru](compilers-element.md) .</span><span class="sxs-lookup"><span data-stu-id="ab24a-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](compilers-element.md) element.</span></span> <span data-ttu-id="ab24a-129">V .NET Framework verze 2,0 nejsou výchozí poskytovatelé jazyků identifikováni v [ \<>](compilers-element.md) elementu compilers, ale lze je <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> vyčíslit pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="ab24a-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="ab24a-130">.NET Framework verze 1,0 a 1,1</span><span class="sxs-lookup"><span data-stu-id="ab24a-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="ab24a-131">Element [System. CodeDom > obsahuje nastavení konfigurace kompilátoru pro poskytovatele jazyků v počítači. \<](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="ab24a-131">The [\<system.codedom>](system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="ab24a-132">Kompilátory > element obsahuje nula nebo více [ \<elementů > kompilátoru](compiler-element.md) . [ \<](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="ab24a-132">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="ab24a-133">[ Každý\<kompilátor >](compiler-element.md) element určuje atributy konfigurace kompilátoru pro konkrétního poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="ab24a-133">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="ab24a-134">.NET Framework definuje počáteční nastavení kompilátoru v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="ab24a-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="ab24a-135">Vývojáři a dodavatelé kompilátoru můžou přidat konfigurační nastavení pro novou <xref:System.CodeDom.Compiler.CodeDomProvider> implementaci.</span><span class="sxs-lookup"><span data-stu-id="ab24a-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="ab24a-136"><xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> Použijte metodu k programovému vytvoření výčtu poskytovatele jazyka a nastavení konfigurace kompilátoru v počítači.</span><span class="sxs-lookup"><span data-stu-id="ab24a-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="ab24a-137">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="ab24a-137">Configuration File</span></span>  
 <span data-ttu-id="ab24a-138">Tento element lze použít v konfiguračním souboru počítače a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="ab24a-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab24a-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="ab24a-139">Example</span></span>  
 <span data-ttu-id="ab24a-140">Následující příklad ilustruje typickou konfiguraci kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="ab24a-140">The following example illustrates a typical compiler configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ab24a-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab24a-141">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="ab24a-142">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="ab24a-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ab24a-143">Schéma nastavení kompilátoru a poskytovatele jazyka</span><span class="sxs-lookup"><span data-stu-id="ab24a-143">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ab24a-144">\<> – element kompilátoru</span><span class="sxs-lookup"><span data-stu-id="ab24a-144">\<compiler> Element</span></span>](compiler-element.md)
