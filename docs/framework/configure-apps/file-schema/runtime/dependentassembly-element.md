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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a0604161ed6e7c3ead4a2e518daebc8414689af
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252710"
---
# <a name="dependentassembly-element"></a><span data-ttu-id="f3fa1-102">\<dependentAssembly – > element</span><span class="sxs-lookup"><span data-stu-id="f3fa1-102">\<dependentAssembly> Element</span></span>
<span data-ttu-id="f3fa1-103">Zapouzdřuje pro jednotlivá sestavení zásady vazeb a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="f3fa1-103">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="f3fa1-104">Pro každé `dependentAssembly` sestavení použijte jeden prvek.</span><span class="sxs-lookup"><span data-stu-id="f3fa1-104">Use one `dependentAssembly` element for each assembly.</span></span>  
  
<span data-ttu-id="f3fa1-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f3fa1-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f3fa1-106">&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="f3fa1-106">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="f3fa1-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="f3fa1-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="f3fa1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> dependentAssembly**</span><span class="sxs-lookup"><span data-stu-id="f3fa1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dependentAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3fa1-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3fa1-109">Syntax</span></span>  
  
```xml  
<dependentAssembly>   
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3fa1-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f3fa1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f3fa1-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f3fa1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3fa1-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="f3fa1-112">Attributes</span></span>  
 <span data-ttu-id="f3fa1-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="f3fa1-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f3fa1-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f3fa1-114">Child Elements</span></span>  
  
|<span data-ttu-id="f3fa1-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="f3fa1-115">Element</span></span>|<span data-ttu-id="f3fa1-116">Popis</span><span class="sxs-lookup"><span data-stu-id="f3fa1-116">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="f3fa1-117">Obsahuje identifikační informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="f3fa1-117">Contains identifying information about the assembly.</span></span> <span data-ttu-id="f3fa1-118">Tento prvek musí být zahrnut v každém `dependentAssembly` elementu.</span><span class="sxs-lookup"><span data-stu-id="f3fa1-118">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="f3fa1-119">Určuje, kde modul runtime může najít sdílené sestavení, pokud není nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="f3fa1-119">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="f3fa1-120">Přesměruje jednu verzi sestavení k jiné.</span><span class="sxs-lookup"><span data-stu-id="f3fa1-120">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="f3fa1-121">Určuje, zda modul runtime používá zásady vydavatele pro toto sestavení.</span><span class="sxs-lookup"><span data-stu-id="f3fa1-121">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f3fa1-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f3fa1-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f3fa1-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="f3fa1-123">Element</span></span>|<span data-ttu-id="f3fa1-124">Popis</span><span class="sxs-lookup"><span data-stu-id="f3fa1-124">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="f3fa1-125">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="f3fa1-125">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="f3fa1-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f3fa1-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f3fa1-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="f3fa1-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f3fa1-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3fa1-128">Example</span></span>  
 <span data-ttu-id="f3fa1-129">Následující příklad ukazuje, jak zapouzdřit informace o sestavení pro dvě sestavení.</span><span class="sxs-lookup"><span data-stu-id="f3fa1-129">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f3fa1-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3fa1-130">See also</span></span>

- [<span data-ttu-id="f3fa1-131">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="f3fa1-131">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f3fa1-132">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="f3fa1-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f3fa1-133">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="f3fa1-133">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
