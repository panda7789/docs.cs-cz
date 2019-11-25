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
ms.openlocfilehash: b09c2a1f67974a67a3f9d58af7cb8cf66a197026
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088701"
---
# <a name="compilers-element"></a><span data-ttu-id="755aa-102">> elementu \<kompilátorů</span><span class="sxs-lookup"><span data-stu-id="755aa-102">\<compilers> Element</span></span>
<span data-ttu-id="755aa-103">Kontejner pro prvky konfigurace kompilátoru; obsahuje nula nebo více [\<> elementy kompilátoru](compiler-element.md) .</span><span class="sxs-lookup"><span data-stu-id="755aa-103">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>  

<span data-ttu-id="755aa-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="755aa-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="755aa-105">&nbsp;&nbsp;[ **\<System. codedom >** ](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="755aa-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span></span>\
<span data-ttu-id="755aa-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<ch kompilátorů >**</span><span class="sxs-lookup"><span data-stu-id="755aa-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<compilers>**</span></span>

## <a name="syntax"></a><span data-ttu-id="755aa-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="755aa-107">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="755aa-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="755aa-108">Attributes and Elements</span></span>  
 <span data-ttu-id="755aa-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="755aa-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="755aa-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="755aa-110">Attributes</span></span>  
 <span data-ttu-id="755aa-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="755aa-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="755aa-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="755aa-112">Child Elements</span></span>  
  
|<span data-ttu-id="755aa-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="755aa-113">Element</span></span>|<span data-ttu-id="755aa-114">Popis</span><span class="sxs-lookup"><span data-stu-id="755aa-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="755aa-115">\<element > kompilátoru</span><span class="sxs-lookup"><span data-stu-id="755aa-115">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="755aa-116">Určuje atributy konfigurace kompilátoru pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="755aa-116">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="755aa-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="755aa-117">Parent Elements</span></span>  
  
|<span data-ttu-id="755aa-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="755aa-118">Element</span></span>|<span data-ttu-id="755aa-119">Popis</span><span class="sxs-lookup"><span data-stu-id="755aa-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="755aa-120">> element konfigurace \<</span><span class="sxs-lookup"><span data-stu-id="755aa-120">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="755aa-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="755aa-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="755aa-122">\<> element System. CodeDom</span><span class="sxs-lookup"><span data-stu-id="755aa-122">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="755aa-123">Určuje nastavení konfigurace kompilátoru pro dostupné poskytovatele jazyků.</span><span class="sxs-lookup"><span data-stu-id="755aa-123">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="755aa-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="755aa-124">Remarks</span></span>  
 <span data-ttu-id="755aa-125">[> Prvek\<compilers](compilers-element.md) obsahuje nastavení konfigurace kompilátoru pro poskytovatele jazyků v počítači.</span><span class="sxs-lookup"><span data-stu-id="755aa-125">The [\<compilers>](compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="755aa-126">Každý [\<kompilátor >](compiler-element.md) prvek určuje atributy konfigurace kompilátoru pro konkrétního poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="755aa-126">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="755aa-127">.NET Framework definuje nastavení počátečního kompilátoru a poskytovatele jazyka v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="755aa-127">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="755aa-128">Vývojáři a dodavatelé kompilátoru můžou přidat konfigurační nastavení pro novou implementaci <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="755aa-128">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="755aa-129">Použijte metodu <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> k programovému vytvoření výčtu poskytovatele jazyka a nastavení konfigurace kompilátoru v počítači.</span><span class="sxs-lookup"><span data-stu-id="755aa-129">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="755aa-130">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="755aa-130">Configuration File</span></span>  
 <span data-ttu-id="755aa-131">Tento element lze použít v konfiguračním souboru počítače a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="755aa-131">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="755aa-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="755aa-132">Example</span></span>  
 <span data-ttu-id="755aa-133">Následující příklad ilustruje typický prvek konfigurace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="755aa-133">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="755aa-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="755aa-134">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="755aa-135">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="755aa-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="755aa-136">Schéma nastavení kompilátoru a poskytovatele jazyka</span><span class="sxs-lookup"><span data-stu-id="755aa-136">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="755aa-137">\<element > kompilátoru</span><span class="sxs-lookup"><span data-stu-id="755aa-137">\<compiler> Element</span></span>](compiler-element.md)
