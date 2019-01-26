---
title: Schéma nastavení kompilátoru a poskytovatele jazyka
ms.date: 03/30/2017
helpviewer_keywords:
- configuration settings [.NET Framework], compilers
- compiler configuration elements, schema
- compiler configuration elements
- language providers
- compiler configuration settings, schema
- configuration schema [.NET Framework], compiler settings
- language providers, settings schema
- compiler configuration settings
ms.assetid: c020b139-8699-4f0d-9ac9-70d0c5b2a8c8
ms.openlocfilehash: ab8225d664b658789f7eb9e7830d5ec527ded94a
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2019
ms.locfileid: "55084364"
---
# <a name="compiler-and-language-provider-settings-schema"></a><span data-ttu-id="db90c-102">Schéma nastavení kompilátoru a poskytovatele jazyka</span><span class="sxs-lookup"><span data-stu-id="db90c-102">Compiler and Language Provider Settings Schema</span></span>
<span data-ttu-id="db90c-103">Nastavení poskytovatele jazyka a kompilátoru zadejte kompilátor – elementy konfigurace pro zprostředkovatele dostupných poskytovatelů jazyka.</span><span class="sxs-lookup"><span data-stu-id="db90c-103">Compiler and language provider settings specify compiler configuration elements for available language providers.</span></span> <span data-ttu-id="db90c-104">Každý prvek konfigurace kompilátor Určuje kód název typu poskytovatele, parametry kompilátoru nepodporuje názvy jazyků a podporované přípony souborů.</span><span class="sxs-lookup"><span data-stu-id="db90c-104">Each compiler configuration element specifies the code provider type name, compiler parameters, supported language names, and supported file extensions.</span></span>  
  
 <span data-ttu-id="db90c-105">Rozhraní .NET Framework definuje počáteční kompilátor – nastavení v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="db90c-105">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="db90c-106">Vývojářům a dodavatelům kompilátoru můžete přidat nastavení konfigurace pro nové <xref:System.CodeDom.Compiler.CodeDomProvider> implementace.</span><span class="sxs-lookup"><span data-stu-id="db90c-106">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="db90c-107">Použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> způsob, jak programově vytvářet výčty zprostředkovatele a kompilátoru konfigurace nastavení jazyka v počítači.</span><span class="sxs-lookup"><span data-stu-id="db90c-107">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
 [<span data-ttu-id="db90c-108">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="db90c-108">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="db90c-109">\<system.codedom></span><span class="sxs-lookup"><span data-stu-id="db90c-109">\<system.codedom></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)  
  
 [<span data-ttu-id="db90c-110">\<compilers></span><span class="sxs-lookup"><span data-stu-id="db90c-110">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
  
 [<span data-ttu-id="db90c-111">\<compiler></span><span class="sxs-lookup"><span data-stu-id="db90c-111">\<compiler></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)  
  
|<span data-ttu-id="db90c-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="db90c-112">Element</span></span>|<span data-ttu-id="db90c-113">Popis</span><span class="sxs-lookup"><span data-stu-id="db90c-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db90c-114">\<system.codedom></span><span class="sxs-lookup"><span data-stu-id="db90c-114">\<system.codedom></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="db90c-115">Určuje konfigurační nastavení kompilátoru pro zprostředkovatele dostupných poskytovatelů jazyka.</span><span class="sxs-lookup"><span data-stu-id="db90c-115">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="db90c-116">\<compilers></span><span class="sxs-lookup"><span data-stu-id="db90c-116">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="db90c-117">Kontejner pro kompilátor – elementy konfigurace; obsahuje nulu nebo více [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="db90c-117">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>|  
|[<span data-ttu-id="db90c-118">\<compiler></span><span class="sxs-lookup"><span data-stu-id="db90c-118">\<compiler></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="db90c-119">Určuje kompilátor – konfigurační atributy pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="db90c-119">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="db90c-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="db90c-120">Example</span></span>  
 <span data-ttu-id="db90c-121">Následující příklad ukazuje prvek typické kompilátoru konfigurace.</span><span class="sxs-lookup"><span data-stu-id="db90c-121">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="db90c-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db90c-122">See also</span></span>
- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="db90c-123">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="db90c-123">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="db90c-124">\<Kompilátor > – Element</span><span class="sxs-lookup"><span data-stu-id="db90c-124">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
