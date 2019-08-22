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
ms.openlocfilehash: 4900c391ae94447cdf4be331a27f6f3398e9129a
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659723"
---
# <a name="compiler-and-language-provider-settings-schema"></a><span data-ttu-id="42835-102">Schéma nastavení kompilátoru a poskytovatele jazyka</span><span class="sxs-lookup"><span data-stu-id="42835-102">Compiler and Language Provider Settings Schema</span></span>
<span data-ttu-id="42835-103">Nastavení zprostředkovatele kompilátoru a jazyka určují prvky konfigurace kompilátoru pro dostupné poskytovatele jazyků.</span><span class="sxs-lookup"><span data-stu-id="42835-103">Compiler and language provider settings specify compiler configuration elements for available language providers.</span></span> <span data-ttu-id="42835-104">Každý prvek konfigurace kompilátoru Určuje název typu poskytovatele kódu, parametry kompilátoru, podporované názvy jazyků a podporovaná rozšíření souborů.</span><span class="sxs-lookup"><span data-stu-id="42835-104">Each compiler configuration element specifies the code provider type name, compiler parameters, supported language names, and supported file extensions.</span></span>  
  
 <span data-ttu-id="42835-105">.NET Framework definuje počáteční nastavení kompilátoru v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="42835-105">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="42835-106">Vývojáři a dodavatelé kompilátoru můžou přidat konfigurační nastavení pro novou <xref:System.CodeDom.Compiler.CodeDomProvider> implementaci.</span><span class="sxs-lookup"><span data-stu-id="42835-106">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="42835-107"><xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> Použijte metodu k programovému vytvoření výčtu poskytovatele jazyka a nastavení konfigurace kompilátoru v počítači.</span><span class="sxs-lookup"><span data-stu-id="42835-107">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
 [<span data-ttu-id="42835-108">\<Element > Konfigurace</span><span class="sxs-lookup"><span data-stu-id="42835-108">\<configuration> Element</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="42835-109">\<system.codedom></span><span class="sxs-lookup"><span data-stu-id="42835-109">\<system.codedom></span></span>](system-codedom-element.md)  
  
 [<span data-ttu-id="42835-110">\<compilers></span><span class="sxs-lookup"><span data-stu-id="42835-110">\<compilers></span></span>](compilers-element.md)  
  
 [<span data-ttu-id="42835-111">\<> kompilátoru</span><span class="sxs-lookup"><span data-stu-id="42835-111">\<compiler></span></span>](compiler-element.md)  
  
|<span data-ttu-id="42835-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="42835-112">Element</span></span>|<span data-ttu-id="42835-113">Popis</span><span class="sxs-lookup"><span data-stu-id="42835-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42835-114">\<system.codedom></span><span class="sxs-lookup"><span data-stu-id="42835-114">\<system.codedom></span></span>](system-codedom-element.md)|<span data-ttu-id="42835-115">Určuje nastavení konfigurace kompilátoru pro dostupné poskytovatele jazyků.</span><span class="sxs-lookup"><span data-stu-id="42835-115">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="42835-116">\<compilers></span><span class="sxs-lookup"><span data-stu-id="42835-116">\<compilers></span></span>](compilers-element.md)|<span data-ttu-id="42835-117">Kontejner pro prvky konfigurace kompilátoru; obsahuje nula nebo více [ \<elementů > kompilátoru](compiler-element.md) .</span><span class="sxs-lookup"><span data-stu-id="42835-117">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
|[<span data-ttu-id="42835-118">\<> kompilátoru</span><span class="sxs-lookup"><span data-stu-id="42835-118">\<compiler></span></span>](compiler-element.md)|<span data-ttu-id="42835-119">Určuje atributy konfigurace kompilátoru pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="42835-119">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="42835-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="42835-120">Example</span></span>  
 <span data-ttu-id="42835-121">Následující příklad ilustruje typický prvek konfigurace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="42835-121">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="42835-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42835-122">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="42835-123">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="42835-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="42835-124">\<> – element kompilátoru</span><span class="sxs-lookup"><span data-stu-id="42835-124">\<compiler> Element</span></span>](compiler-element.md)
