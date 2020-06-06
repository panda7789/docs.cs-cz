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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155411"
---
# <a name="compilers-element"></a><span data-ttu-id="cc1cb-102">Element \<compilers></span><span class="sxs-lookup"><span data-stu-id="cc1cb-102">\<compilers> Element</span></span>
<span data-ttu-id="cc1cb-103">Kontejner pro prvky konfigurace kompilátoru; obsahuje nula nebo více [\<compiler>](compiler-element.md) prvků.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-103">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<compilers>**

## <a name="syntax"></a><span data-ttu-id="cc1cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc1cb-104">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc1cb-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cc1cb-105">Attributes and Elements</span></span>  
 <span data-ttu-id="cc1cb-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc1cb-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="cc1cb-107">Attributes</span></span>  
 <span data-ttu-id="cc1cb-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="cc1cb-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cc1cb-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cc1cb-109">Child Elements</span></span>  
  
|<span data-ttu-id="cc1cb-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="cc1cb-110">Element</span></span>|<span data-ttu-id="cc1cb-111">Description</span><span class="sxs-lookup"><span data-stu-id="cc1cb-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc1cb-112">\<compiler>Objekt</span><span class="sxs-lookup"><span data-stu-id="cc1cb-112">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="cc1cb-113">Určuje atributy konfigurace kompilátoru pro poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-113">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cc1cb-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cc1cb-114">Parent Elements</span></span>  
  
|<span data-ttu-id="cc1cb-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="cc1cb-115">Element</span></span>|<span data-ttu-id="cc1cb-116">Description</span><span class="sxs-lookup"><span data-stu-id="cc1cb-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc1cb-117">\<configuration>Objekt</span><span class="sxs-lookup"><span data-stu-id="cc1cb-117">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="cc1cb-118">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="cc1cb-119">\<system.codedom>Objekt</span><span class="sxs-lookup"><span data-stu-id="cc1cb-119">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="cc1cb-120">Určuje nastavení konfigurace kompilátoru pro dostupné poskytovatele jazyků.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-120">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc1cb-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cc1cb-121">Remarks</span></span>  
 <span data-ttu-id="cc1cb-122">[\<compilers>](compilers-element.md)Element obsahuje nastavení konfigurace kompilátoru pro poskytovatele jazyků v počítači.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-122">The [\<compilers>](compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="cc1cb-123">Každý [\<compiler>](compiler-element.md) prvek určuje atributy konfigurace kompilátoru pro konkrétního poskytovatele jazyka.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-123">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="cc1cb-124">.NET Framework definuje nastavení počátečního kompilátoru a poskytovatele jazyka v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="cc1cb-124">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="cc1cb-125">Vývojáři a dodavatelé kompilátoru můžou přidat konfigurační nastavení pro novou <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementaci.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-125">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="cc1cb-126">Použijte <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metodu k programovému vytvoření výčtu poskytovatele jazyka a nastavení konfigurace kompilátoru v počítači.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-126">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="cc1cb-127">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="cc1cb-127">Configuration File</span></span>  
 <span data-ttu-id="cc1cb-128">Tento element lze použít v konfiguračním souboru počítače a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-128">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc1cb-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="cc1cb-129">Example</span></span>  
 <span data-ttu-id="cc1cb-130">Následující příklad ilustruje typický prvek konfigurace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="cc1cb-130">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cc1cb-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc1cb-131">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="cc1cb-132">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="cc1cb-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="cc1cb-133">Schéma nastavení kompilátoru a poskytovatele jazyka</span><span class="sxs-lookup"><span data-stu-id="cc1cb-133">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cc1cb-134">\<compiler>Objekt</span><span class="sxs-lookup"><span data-stu-id="cc1cb-134">\<compiler> Element</span></span>](compiler-element.md)
