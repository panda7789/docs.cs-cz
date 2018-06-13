---
title: '&lt;Kompilátory&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fc85610f5c3db7929f824fda2dd211300d9b05c1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742988"
---
# <a name="ltcompilersgt-element"></a><span data-ttu-id="a144f-102">&lt;Kompilátory&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="a144f-102">&lt;compilers&gt; Element</span></span>
<span data-ttu-id="a144f-103">Kontejner pro kompilátor – elementy konfigurace; obsahuje nula nebo více [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="a144f-103">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>  
  
 <span data-ttu-id="a144f-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="a144f-104">\<configuration></span></span>  
<span data-ttu-id="a144f-105">\<System.CodeDom – ></span><span class="sxs-lookup"><span data-stu-id="a144f-105">\<system.codedom></span></span>  
<span data-ttu-id="a144f-106">\<Kompilátory > elementu</span><span class="sxs-lookup"><span data-stu-id="a144f-106">\<compilers> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a144f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a144f-107">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a144f-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a144f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a144f-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a144f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a144f-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="a144f-110">Attributes</span></span>  
 <span data-ttu-id="a144f-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="a144f-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a144f-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a144f-112">Child Elements</span></span>  
  
|<span data-ttu-id="a144f-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="a144f-113">Element</span></span>|<span data-ttu-id="a144f-114">Popis</span><span class="sxs-lookup"><span data-stu-id="a144f-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a144f-115">\<kompilátoru > elementu</span><span class="sxs-lookup"><span data-stu-id="a144f-115">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="a144f-116">Kompilátor – konfigurační atributy Určuje jazyk zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="a144f-116">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a144f-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a144f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a144f-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="a144f-118">Element</span></span>|<span data-ttu-id="a144f-119">Popis</span><span class="sxs-lookup"><span data-stu-id="a144f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a144f-120">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="a144f-120">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="a144f-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a144f-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="a144f-122">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="a144f-122">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="a144f-123">Určuje kompilátor – nastavení konfigurace pro zprostředkovatele dostupný jazyk.</span><span class="sxs-lookup"><span data-stu-id="a144f-123">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a144f-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a144f-124">Remarks</span></span>  
 <span data-ttu-id="a144f-125">[ \<Kompilátory >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element obsahuje konfigurační nastavení kompilátoru pro zprostředkovatelé jazyka v počítači.</span><span class="sxs-lookup"><span data-stu-id="a144f-125">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="a144f-126">Každý [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element určuje kompilátor – konfigurační atributy pro konkrétní jazyk zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="a144f-126">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="a144f-127">Rozhraní .NET Framework definuje počáteční kompilátoru a poskytovatele nastavení jazyka v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="a144f-127">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="a144f-128">Vývojářům a dodavatelům kompilátoru můžete přidat nastavení konfigurace pro novou <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementace.</span><span class="sxs-lookup"><span data-stu-id="a144f-128">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="a144f-129">Použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metoda prostřednictvím kódu programu výčet zprostředkovatele a kompilátoru konfigurace nastavení jazyka v počítači.</span><span class="sxs-lookup"><span data-stu-id="a144f-129">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="a144f-130">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="a144f-130">Configuration File</span></span>  
 <span data-ttu-id="a144f-131">Tento element lze v konfiguračním souboru počítače a konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="a144f-131">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a144f-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="a144f-132">Example</span></span>  
 <span data-ttu-id="a144f-133">Následující příklad ukazuje prvek typické kompilátoru konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a144f-133">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a144f-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="a144f-134">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="a144f-135">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="a144f-135">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="a144f-136">Schéma nastavení kompilátoru a poskytovatele jazyka</span><span class="sxs-lookup"><span data-stu-id="a144f-136">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 [<span data-ttu-id="a144f-137">\<kompilátoru > elementu</span><span class="sxs-lookup"><span data-stu-id="a144f-137">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
