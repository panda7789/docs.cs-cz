---
title: '&lt;zjišťování&gt; – Element'
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
ms.openlocfilehash: a5b9be3050da21c0a99931ca70cf990b0b8bf1fe
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612299"
---
# <a name="ltprobinggt-element"></a><span data-ttu-id="60d81-102">&lt;zjišťování&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="60d81-102">&lt;probing&gt; Element</span></span>
<span data-ttu-id="60d81-103">Určuje základní podadresářích aplikace pro modul common language runtime pro hledání při načítání sestavení.</span><span class="sxs-lookup"><span data-stu-id="60d81-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
 <span data-ttu-id="60d81-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="60d81-104">\<configuration></span></span>  
<span data-ttu-id="60d81-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="60d81-105">\<runtime></span></span>  
<span data-ttu-id="60d81-106">\<assemblybinding – ></span><span class="sxs-lookup"><span data-stu-id="60d81-106">\<assemblyBinding></span></span>  
<span data-ttu-id="60d81-107">\<zjišťování ></span><span class="sxs-lookup"><span data-stu-id="60d81-107">\<probing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60d81-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60d81-108">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60d81-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="60d81-109">Attributes and Elements</span></span>  
 <span data-ttu-id="60d81-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="60d81-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60d81-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="60d81-111">Attributes</span></span>  
  
|<span data-ttu-id="60d81-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="60d81-112">Attribute</span></span>|<span data-ttu-id="60d81-113">Popis</span><span class="sxs-lookup"><span data-stu-id="60d81-113">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="60d81-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="60d81-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="60d81-115">Určuje podadresáře základního adresáře aplikace, které mohou obsahovat sestavení.</span><span class="sxs-lookup"><span data-stu-id="60d81-115">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="60d81-116">Vymezení každý podadresář oddělte středníkem.</span><span class="sxs-lookup"><span data-stu-id="60d81-116">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="60d81-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="60d81-117">Child Elements</span></span>  
 <span data-ttu-id="60d81-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="60d81-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="60d81-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="60d81-119">Parent Elements</span></span>  
  
|<span data-ttu-id="60d81-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="60d81-120">Element</span></span>|<span data-ttu-id="60d81-121">Popis</span><span class="sxs-lookup"><span data-stu-id="60d81-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="60d81-122">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="60d81-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="60d81-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="60d81-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="60d81-124">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="60d81-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="60d81-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="60d81-125">Example</span></span>  
 <span data-ttu-id="60d81-126">Následující příklad ukazuje, jak určit základní podadresářích aplikace, které by měl modul runtime vyhledat sestavení.</span><span class="sxs-lookup"><span data-stu-id="60d81-126">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="60d81-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="60d81-127">See Also</span></span>  
- [<span data-ttu-id="60d81-128">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="60d81-128">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="60d81-129">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="60d81-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="60d81-130">Určení umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="60d81-130">Specifying an Assembly's Location</span></span>](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
- [<span data-ttu-id="60d81-131">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="60d81-131">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
