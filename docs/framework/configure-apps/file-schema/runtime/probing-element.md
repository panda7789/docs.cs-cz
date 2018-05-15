---
title: '&lt;Zkušební fáze&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing
- http://schemas.microsoft.com/.NetConfiguration/v2.0#probing
helpviewer_keywords:
- <probing> element
- container tags, <probing> element
- probing element
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cab16e83466b5954bfebac07dd79c9a8b5e4594
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltprobinggt-element"></a><span data-ttu-id="d4e4c-102">&lt;Zkušební fáze&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="d4e4c-102">&lt;probing&gt; Element</span></span>
<span data-ttu-id="d4e4c-103">Určuje základní podadresáře aplikace pro modul common language runtime pro vyhledávání při načítání sestavení.</span><span class="sxs-lookup"><span data-stu-id="d4e4c-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
 <span data-ttu-id="d4e4c-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="d4e4c-104">\<configuration></span></span>  
<span data-ttu-id="d4e4c-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="d4e4c-105">\<runtime></span></span>  
<span data-ttu-id="d4e4c-106">\<assemblybinding – ></span><span class="sxs-lookup"><span data-stu-id="d4e4c-106">\<assemblyBinding></span></span>  
<span data-ttu-id="d4e4c-107">\<Zkušební fáze ></span><span class="sxs-lookup"><span data-stu-id="d4e4c-107">\<probing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4e4c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4e4c-108">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4e4c-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d4e4c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d4e4c-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d4e4c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4e4c-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="d4e4c-111">Attributes</span></span>  
  
|<span data-ttu-id="d4e4c-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="d4e4c-112">Attribute</span></span>|<span data-ttu-id="d4e4c-113">Popis</span><span class="sxs-lookup"><span data-stu-id="d4e4c-113">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="d4e4c-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="d4e4c-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="d4e4c-115">Určuje základní adresáře aplikace, který může obsahovat sestavení.</span><span class="sxs-lookup"><span data-stu-id="d4e4c-115">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="d4e4c-116">Omezte každý podadresáři středníkem.</span><span class="sxs-lookup"><span data-stu-id="d4e4c-116">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4e4c-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d4e4c-117">Child Elements</span></span>  
 <span data-ttu-id="d4e4c-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="d4e4c-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4e4c-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d4e4c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d4e4c-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="d4e4c-120">Element</span></span>|<span data-ttu-id="d4e4c-121">Popis</span><span class="sxs-lookup"><span data-stu-id="d4e4c-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="d4e4c-122">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="d4e4c-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="d4e4c-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d4e4c-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d4e4c-124">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d4e4c-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d4e4c-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="d4e4c-125">Example</span></span>  
 <span data-ttu-id="d4e4c-126">Následující příklad ukazuje, jak zadat základní podadresářích aplikace, které modul runtime program hledat sestavení.</span><span class="sxs-lookup"><span data-stu-id="d4e4c-126">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4e4c-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4e4c-127">See Also</span></span>  
 [<span data-ttu-id="d4e4c-128">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="d4e4c-128">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="d4e4c-129">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="d4e4c-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="d4e4c-130">Určení umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="d4e4c-130">Specifying an Assembly's Location</span></span>](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
 [<span data-ttu-id="d4e4c-131">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="d4e4c-131">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
