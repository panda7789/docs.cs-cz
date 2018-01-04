---
title: "&lt;dependentAssembly&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#dependentAssembly
helpviewer_keywords:
- container tags, <dependentAssembly> element
- dependentAssembly element
- <dependentAssembly> element
ms.assetid: 14e95627-dd79-4b82-ac85-e682aa3a31d8
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a968d2d1abf6e77cddd9d0a0367822ee4f9723ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltdependentassemblygt-element"></a><span data-ttu-id="93bee-102">&lt;dependentAssembly&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="93bee-102">&lt;dependentAssembly&gt; Element</span></span>
<span data-ttu-id="93bee-103">Zapouzdřuje pro jednotlivá sestavení zásady vazeb a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="93bee-103">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="93bee-104">Použijte jednu `dependentAssembly` element pro každé sestavení.</span><span class="sxs-lookup"><span data-stu-id="93bee-104">Use one `dependentAssembly` element for each assembly.</span></span>  
  
 <span data-ttu-id="93bee-105">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="93bee-105">\<configuration></span></span>  
<span data-ttu-id="93bee-106">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="93bee-106">\<runtime></span></span>  
<span data-ttu-id="93bee-107">\<assemblybinding – ></span><span class="sxs-lookup"><span data-stu-id="93bee-107">\<assemblyBinding></span></span>  
<span data-ttu-id="93bee-108">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="93bee-108">\<dependentAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93bee-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93bee-109">Syntax</span></span>  
  
```xml  
<dependentAssembly>   
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93bee-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="93bee-110">Attributes and Elements</span></span>  
 <span data-ttu-id="93bee-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="93bee-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93bee-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="93bee-112">Attributes</span></span>  
 <span data-ttu-id="93bee-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="93bee-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="93bee-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="93bee-114">Child Elements</span></span>  
  
|<span data-ttu-id="93bee-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="93bee-115">Element</span></span>|<span data-ttu-id="93bee-116">Popis</span><span class="sxs-lookup"><span data-stu-id="93bee-116">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="93bee-117">Obsahuje identifikační informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="93bee-117">Contains identifying information about the assembly.</span></span> <span data-ttu-id="93bee-118">Tento element musí být součástí každé `dependentAssembly` elementu.</span><span class="sxs-lookup"><span data-stu-id="93bee-118">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="93bee-119">Určuje, kde modulu runtime můžete najít sdílené sestavení, pokud není nainstalovaná v počítači.</span><span class="sxs-lookup"><span data-stu-id="93bee-119">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="93bee-120">Přesměruje jednu verzi sestavení k jiné.</span><span class="sxs-lookup"><span data-stu-id="93bee-120">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="93bee-121">Určuje, zda modul runtime platí pro toto sestavení zásady vydavatele.</span><span class="sxs-lookup"><span data-stu-id="93bee-121">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="93bee-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="93bee-122">Parent Elements</span></span>  
  
|<span data-ttu-id="93bee-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="93bee-123">Element</span></span>|<span data-ttu-id="93bee-124">Popis</span><span class="sxs-lookup"><span data-stu-id="93bee-124">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="93bee-125">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="93bee-125">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="93bee-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="93bee-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="93bee-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="93bee-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="93bee-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="93bee-128">Example</span></span>  
 <span data-ttu-id="93bee-129">Následující příklad ukazuje, jak má být zapouzdřena informací o sestavení pro dvě sestavení.</span><span class="sxs-lookup"><span data-stu-id="93bee-129">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="93bee-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="93bee-130">See Also</span></span>  
 [<span data-ttu-id="93bee-131">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="93bee-131">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="93bee-132">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="93bee-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="93bee-133">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="93bee-133">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
