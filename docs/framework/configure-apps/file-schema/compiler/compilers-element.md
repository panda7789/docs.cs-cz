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
ms.openlocfilehash: 09b1efe321c39402c9280eda0e9def9112462470
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155411"
---
# <a name="compilers-element"></a><span data-ttu-id="b709f-102">\<kompilátory> Element</span><span class="sxs-lookup"><span data-stu-id="b709f-102">\<compilers> Element</span></span>
<span data-ttu-id="b709f-103">Kontejner pro konfigurační prvky kompilátoru; obsahuje nula [ \<](compiler-element.md) nebo více>prvků kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="b709f-103">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>  

<span data-ttu-id="b709f-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b709f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b709f-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="b709f-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span></span>\
<span data-ttu-id="b709f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<>kompilátorů**</span><span class="sxs-lookup"><span data-stu-id="b709f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<compilers>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b709f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b709f-107">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b709f-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b709f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b709f-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b709f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b709f-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="b709f-110">Attributes</span></span>  
 <span data-ttu-id="b709f-111">Žádné.</span><span class="sxs-lookup"><span data-stu-id="b709f-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b709f-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b709f-112">Child Elements</span></span>  
  
|<span data-ttu-id="b709f-113">Element</span><span class="sxs-lookup"><span data-stu-id="b709f-113">Element</span></span>|<span data-ttu-id="b709f-114">Popis</span><span class="sxs-lookup"><span data-stu-id="b709f-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b709f-115">\<> element kompilátoru</span><span class="sxs-lookup"><span data-stu-id="b709f-115">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="b709f-116">Určuje atributy konfigurace kompilátoru pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="b709f-116">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b709f-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b709f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b709f-118">Element</span><span class="sxs-lookup"><span data-stu-id="b709f-118">Element</span></span>|<span data-ttu-id="b709f-119">Popis</span><span class="sxs-lookup"><span data-stu-id="b709f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b709f-120">\<konfigurace> Element</span><span class="sxs-lookup"><span data-stu-id="b709f-120">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="b709f-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b709f-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="b709f-122">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="b709f-122">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="b709f-123">Určuje nastavení konfigurace kompilátoru pro dostupné poskytovatele jazyků.</span><span class="sxs-lookup"><span data-stu-id="b709f-123">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b709f-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b709f-124">Remarks</span></span>  
 <span data-ttu-id="b709f-125">[ \<Kompilátory>](compilers-element.md) prvek obsahuje nastavení konfigurace kompilátoru pro poskytovatele jazyků v počítači.</span><span class="sxs-lookup"><span data-stu-id="b709f-125">The [\<compilers>](compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="b709f-126">Každý [ \<prvek>kompilátoru](compiler-element.md) určuje atributy konfigurace kompilátoru pro konkrétního poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="b709f-126">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="b709f-127">Rozhraní .NET Framework definuje počáteční nastavení kompilátoru a poskytovatele jazyka v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="b709f-127">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="b709f-128">Vývojáři a dodavatelé kompilátoru <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> mohou přidat nastavení konfigurace pro novou implementaci.</span><span class="sxs-lookup"><span data-stu-id="b709f-128">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="b709f-129">Pomocí <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> této metody můžete programově vytvořit výčet nastavení poskytovatele jazyka a konfigurace kompilátoru v počítači.</span><span class="sxs-lookup"><span data-stu-id="b709f-129">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="b709f-130">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="b709f-130">Configuration File</span></span>  
 <span data-ttu-id="b709f-131">Tento prvek lze použít v konfiguračním souboru počítače a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="b709f-131">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b709f-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="b709f-132">Example</span></span>  
 <span data-ttu-id="b709f-133">Následující příklad ilustruje typický konfigurační prvek kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="b709f-133">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b709f-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="b709f-134">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="b709f-135">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b709f-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b709f-136">Schéma nastavení kompilátoru a poskytovatele jazyka</span><span class="sxs-lookup"><span data-stu-id="b709f-136">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b709f-137">\<> element kompilátoru</span><span class="sxs-lookup"><span data-stu-id="b709f-137">\<compiler> Element</span></span>](compiler-element.md)
