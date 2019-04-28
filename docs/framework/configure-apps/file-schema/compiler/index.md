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
ms.openlocfilehash: fe08ac5dc0600e0861bb349ce99875af8658eb4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675270"
---
# <a name="compiler-and-language-provider-settings-schema"></a><span data-ttu-id="36507-102">Schéma nastavení kompilátoru a poskytovatele jazyka</span><span class="sxs-lookup"><span data-stu-id="36507-102">Compiler and Language Provider Settings Schema</span></span>
<span data-ttu-id="36507-103">Nastavení poskytovatele jazyka a kompilátoru zadejte kompilátor – elementy konfigurace pro zprostředkovatele dostupných poskytovatelů jazyka.</span><span class="sxs-lookup"><span data-stu-id="36507-103">Compiler and language provider settings specify compiler configuration elements for available language providers.</span></span> <span data-ttu-id="36507-104">Každý prvek konfigurace kompilátor Určuje kód název typu poskytovatele, parametry kompilátoru nepodporuje názvy jazyků a podporované přípony souborů.</span><span class="sxs-lookup"><span data-stu-id="36507-104">Each compiler configuration element specifies the code provider type name, compiler parameters, supported language names, and supported file extensions.</span></span>  
  
 <span data-ttu-id="36507-105">Rozhraní .NET Framework definuje počáteční kompilátor – nastavení v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="36507-105">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="36507-106">Vývojářům a dodavatelům kompilátoru můžete přidat nastavení konfigurace pro nové <xref:System.CodeDom.Compiler.CodeDomProvider> implementace.</span><span class="sxs-lookup"><span data-stu-id="36507-106">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="36507-107">Použití <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> způsob, jak programově vytvářet výčty zprostředkovatele a kompilátoru konfigurace nastavení jazyka v počítači.</span><span class="sxs-lookup"><span data-stu-id="36507-107">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
 [<span data-ttu-id="36507-108">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="36507-108">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="36507-109">\<system.codedom></span><span class="sxs-lookup"><span data-stu-id="36507-109">\<system.codedom></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)  
  
 [<span data-ttu-id="36507-110">\<compilers></span><span class="sxs-lookup"><span data-stu-id="36507-110">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
  
 [<span data-ttu-id="36507-111">\<compiler></span><span class="sxs-lookup"><span data-stu-id="36507-111">\<compiler></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)  
  
|<span data-ttu-id="36507-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="36507-112">Element</span></span>|<span data-ttu-id="36507-113">Popis</span><span class="sxs-lookup"><span data-stu-id="36507-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36507-114">\<system.codedom></span><span class="sxs-lookup"><span data-stu-id="36507-114">\<system.codedom></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="36507-115">Určuje konfigurační nastavení kompilátoru pro zprostředkovatele dostupných poskytovatelů jazyka.</span><span class="sxs-lookup"><span data-stu-id="36507-115">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="36507-116">\<compilers></span><span class="sxs-lookup"><span data-stu-id="36507-116">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="36507-117">Kontejner pro kompilátor – elementy konfigurace; obsahuje nulu nebo více [ \<kompilátoru >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="36507-117">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>|  
|[<span data-ttu-id="36507-118">\<compiler></span><span class="sxs-lookup"><span data-stu-id="36507-118">\<compiler></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="36507-119">Určuje kompilátor – konfigurační atributy pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="36507-119">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="36507-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="36507-120">Example</span></span>  
 <span data-ttu-id="36507-121">Následující příklad ukazuje prvek typické kompilátoru konfigurace.</span><span class="sxs-lookup"><span data-stu-id="36507-121">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="36507-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="36507-122">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="36507-123">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="36507-123">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="36507-124">\<Kompilátor > – Element</span><span class="sxs-lookup"><span data-stu-id="36507-124">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
