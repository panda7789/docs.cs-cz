---
title: Element <dependentAssembly>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#dependentAssembly
helpviewer_keywords:
- container tags, <dependentAssembly> element
- dependentAssembly element
- <dependentAssembly> element
ms.assetid: 14e95627-dd79-4b82-ac85-e682aa3a31d8
ms.openlocfilehash: 2de8c752867d00708173d11d1851f415a2e8518d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154202"
---
# <a name="dependentassembly-element"></a><span data-ttu-id="a4a64-102">\<dependentAssembly> Element</span><span class="sxs-lookup"><span data-stu-id="a4a64-102">\<dependentAssembly> Element</span></span>
<span data-ttu-id="a4a64-103">Zapouzdřuje pro jednotlivá sestavení zásady vazeb a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="a4a64-103">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="a4a64-104">Pro `dependentAssembly` každé sestavení použijte jeden prvek.</span><span class="sxs-lookup"><span data-stu-id="a4a64-104">Use one `dependentAssembly` element for each assembly.</span></span>  
  
<span data-ttu-id="a4a64-105">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a4a64-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a4a64-106">&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="a4a64-106">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="a4a64-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="a4a64-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="a4a64-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dependentAssembly>**</span><span class="sxs-lookup"><span data-stu-id="a4a64-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dependentAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4a64-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4a64-109">Syntax</span></span>  
  
```xml  
<dependentAssembly>
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4a64-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a4a64-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a4a64-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a4a64-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4a64-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="a4a64-112">Attributes</span></span>  
 <span data-ttu-id="a4a64-113">Žádné.</span><span class="sxs-lookup"><span data-stu-id="a4a64-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a4a64-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a4a64-114">Child Elements</span></span>  
  
|<span data-ttu-id="a4a64-115">Element</span><span class="sxs-lookup"><span data-stu-id="a4a64-115">Element</span></span>|<span data-ttu-id="a4a64-116">Popis</span><span class="sxs-lookup"><span data-stu-id="a4a64-116">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="a4a64-117">Obsahuje identifikační informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="a4a64-117">Contains identifying information about the assembly.</span></span> <span data-ttu-id="a4a64-118">Tento prvek musí být `dependentAssembly` součástí každého prvku.</span><span class="sxs-lookup"><span data-stu-id="a4a64-118">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="a4a64-119">Určuje, kde může runtime najít sdílené sestavení, pokud není v počítači nainstalováno.</span><span class="sxs-lookup"><span data-stu-id="a4a64-119">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="a4a64-120">Přesměruje jednu verzi sestavení k jiné.</span><span class="sxs-lookup"><span data-stu-id="a4a64-120">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="a4a64-121">Určuje, zda program runtime použije zásadu vydavatele pro toto sestavení.</span><span class="sxs-lookup"><span data-stu-id="a4a64-121">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a4a64-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a4a64-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a4a64-123">Element</span><span class="sxs-lookup"><span data-stu-id="a4a64-123">Element</span></span>|<span data-ttu-id="a4a64-124">Popis</span><span class="sxs-lookup"><span data-stu-id="a4a64-124">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="a4a64-125">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="a4a64-125">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="a4a64-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a4a64-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a4a64-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="a4a64-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a4a64-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4a64-128">Example</span></span>  
 <span data-ttu-id="a4a64-129">Následující příklad ukazuje, jak zapouzdřit informace o sestavení pro dvě sestavení.</span><span class="sxs-lookup"><span data-stu-id="a4a64-129">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="mySecondAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for mySecondAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4a64-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4a64-130">See also</span></span>

- [<span data-ttu-id="a4a64-131">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="a4a64-131">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a4a64-132">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="a4a64-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a4a64-133">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="a4a64-133">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
