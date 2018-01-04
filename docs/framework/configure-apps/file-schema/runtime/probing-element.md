---
title: "&lt;Zkušební fáze&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing
- http://schemas.microsoft.com/.NetConfiguration/v2.0#probing
helpviewer_keywords:
- <probing> element
- container tags, <probing> element
- probing element
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e846cb1386dc64161d91ab50b6a04e5560e9c6da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltprobinggt-element"></a><span data-ttu-id="b27be-102">&lt;Zkušební fáze&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="b27be-102">&lt;probing&gt; Element</span></span>
<span data-ttu-id="b27be-103">Určuje základní podadresáře aplikace pro modul common language runtime pro vyhledávání při načítání sestavení.</span><span class="sxs-lookup"><span data-stu-id="b27be-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
 <span data-ttu-id="b27be-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="b27be-104">\<configuration></span></span>  
<span data-ttu-id="b27be-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="b27be-105">\<runtime></span></span>  
<span data-ttu-id="b27be-106">\<assemblybinding – ></span><span class="sxs-lookup"><span data-stu-id="b27be-106">\<assemblyBinding></span></span>  
<span data-ttu-id="b27be-107">\<Zkušební fáze ></span><span class="sxs-lookup"><span data-stu-id="b27be-107">\<probing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b27be-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b27be-108">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b27be-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b27be-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b27be-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b27be-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b27be-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="b27be-111">Attributes</span></span>  
  
|<span data-ttu-id="b27be-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="b27be-112">Attribute</span></span>|<span data-ttu-id="b27be-113">Popis</span><span class="sxs-lookup"><span data-stu-id="b27be-113">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="b27be-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="b27be-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="b27be-115">Určuje základní adresáře aplikace, který může obsahovat sestavení.</span><span class="sxs-lookup"><span data-stu-id="b27be-115">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="b27be-116">Omezte každý podadresáři středníkem.</span><span class="sxs-lookup"><span data-stu-id="b27be-116">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b27be-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b27be-117">Child Elements</span></span>  
 <span data-ttu-id="b27be-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="b27be-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b27be-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b27be-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b27be-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="b27be-120">Element</span></span>|<span data-ttu-id="b27be-121">Popis</span><span class="sxs-lookup"><span data-stu-id="b27be-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="b27be-122">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="b27be-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="b27be-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b27be-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b27be-124">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="b27be-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b27be-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="b27be-125">Example</span></span>  
 <span data-ttu-id="b27be-126">Následující příklad ukazuje, jak zadat základní podadresářích aplikace, které modul runtime program hledat sestavení.</span><span class="sxs-lookup"><span data-stu-id="b27be-126">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b27be-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="b27be-127">See Also</span></span>  
 [<span data-ttu-id="b27be-128">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="b27be-128">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="b27be-129">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b27be-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="b27be-130">Určení umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="b27be-130">Specifying an Assembly's Location</span></span>](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
 [<span data-ttu-id="b27be-131">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="b27be-131">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
