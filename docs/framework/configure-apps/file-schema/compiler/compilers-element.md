---
title: Element <compilers>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: 744ef0d9bc58e6a0152dce53c40c24eb5283dc0f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705334"
---
# <a name="compilers-element"></a><span data-ttu-id="d42c2-102">\<Kompilátory > – Element</span><span class="sxs-lookup"><span data-stu-id="d42c2-102">\<compilers> Element</span></span>
<span data-ttu-id="d42c2-103">Kontejner pro kompilátor – elementy konfigurace; obsahuje nulu nebo více [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="d42c2-103">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>  
  
 <span data-ttu-id="d42c2-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="d42c2-104">\<configuration></span></span>  
<span data-ttu-id="d42c2-105">\<system.codedom></span><span class="sxs-lookup"><span data-stu-id="d42c2-105">\<system.codedom></span></span>  
<span data-ttu-id="d42c2-106">\<Kompilátory > – Element</span><span class="sxs-lookup"><span data-stu-id="d42c2-106">\<compilers> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d42c2-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d42c2-107">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d42c2-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d42c2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d42c2-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d42c2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d42c2-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="d42c2-110">Attributes</span></span>  
 <span data-ttu-id="d42c2-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="d42c2-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d42c2-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d42c2-112">Child Elements</span></span>  
  
|<span data-ttu-id="d42c2-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="d42c2-113">Element</span></span>|<span data-ttu-id="d42c2-114">Popis</span><span class="sxs-lookup"><span data-stu-id="d42c2-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d42c2-115">\<Kompilátor > – Element</span><span class="sxs-lookup"><span data-stu-id="d42c2-115">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="d42c2-116">Určuje kompilátor – konfigurační atributy pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="d42c2-116">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d42c2-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d42c2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d42c2-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="d42c2-118">Element</span></span>|<span data-ttu-id="d42c2-119">Popis</span><span class="sxs-lookup"><span data-stu-id="d42c2-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d42c2-120">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="d42c2-120">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="d42c2-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d42c2-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="d42c2-122">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="d42c2-122">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="d42c2-123">Určuje konfigurační nastavení kompilátoru pro zprostředkovatele dostupných poskytovatelů jazyka.</span><span class="sxs-lookup"><span data-stu-id="d42c2-123">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d42c2-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d42c2-124">Remarks</span></span>  
 <span data-ttu-id="d42c2-125">[ \<Compilers >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element obsahuje konfigurační nastavení kompilátoru pro poskytovatele jazyka v počítači.</span><span class="sxs-lookup"><span data-stu-id="d42c2-125">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="d42c2-126">Každý [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) prvek určuje kompilátor – konfigurační atributy pro konkrétní jazyk zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="d42c2-126">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="d42c2-127">Rozhraní .NET Framework definuje počáteční kompilátoru a poskytovatele nastavení jazyka v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="d42c2-127">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="d42c2-128">Vývojářům a dodavatelům kompilátoru můžete přidat nastavení konfigurace pro nové <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementace.</span><span class="sxs-lookup"><span data-stu-id="d42c2-128">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="d42c2-129">Použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> způsob, jak programově vytvářet výčty zprostředkovatele a kompilátoru konfigurace nastavení jazyka v počítači.</span><span class="sxs-lookup"><span data-stu-id="d42c2-129">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="d42c2-130">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="d42c2-130">Configuration File</span></span>  
 <span data-ttu-id="d42c2-131">Tento element lze použít v konfiguračním souboru počítače a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="d42c2-131">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d42c2-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="d42c2-132">Example</span></span>  
 <span data-ttu-id="d42c2-133">Následující příklad ukazuje prvek typické kompilátoru konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d42c2-133">The following example illustrates a typical compiler configuration element.</span></span>  
  
```xml  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler   
          language="c#;cs;csharp"   
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""    
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d42c2-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d42c2-134">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="d42c2-135">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="d42c2-135">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="d42c2-136">Schéma nastavení kompilátoru a poskytovatele jazyka</span><span class="sxs-lookup"><span data-stu-id="d42c2-136">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)
- [<span data-ttu-id="d42c2-137">\<Kompilátor > – Element</span><span class="sxs-lookup"><span data-stu-id="d42c2-137">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
