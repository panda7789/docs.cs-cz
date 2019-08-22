---
title: Element <probing>
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
ms.openlocfilehash: 2b00a5349e22feb3cce404ff504edd798ff9e304
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663527"
---
# <a name="probing-element"></a><span data-ttu-id="b578d-102">\<> element zjišťování</span><span class="sxs-lookup"><span data-stu-id="b578d-102">\<probing> Element</span></span>
<span data-ttu-id="b578d-103">Určuje základní podadresáře aplikace pro modul CLR (Common Language Runtime), který se má při načítání sestavení vyhledat.</span><span class="sxs-lookup"><span data-stu-id="b578d-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
 <span data-ttu-id="b578d-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="b578d-104">\<configuration></span></span>  
<span data-ttu-id="b578d-105">\<> modulu runtime</span><span class="sxs-lookup"><span data-stu-id="b578d-105">\<runtime></span></span>  
<span data-ttu-id="b578d-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="b578d-106">\<assemblyBinding></span></span>  
<span data-ttu-id="b578d-107">\<> zjišťování</span><span class="sxs-lookup"><span data-stu-id="b578d-107">\<probing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b578d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b578d-108">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b578d-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b578d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b578d-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b578d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b578d-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="b578d-111">Attributes</span></span>  
  
|<span data-ttu-id="b578d-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="b578d-112">Attribute</span></span>|<span data-ttu-id="b578d-113">Popis</span><span class="sxs-lookup"><span data-stu-id="b578d-113">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="b578d-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="b578d-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="b578d-115">Určuje podadresáře základního adresáře aplikace, který může obsahovat sestavení.</span><span class="sxs-lookup"><span data-stu-id="b578d-115">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="b578d-116">Jednotlivé podadresáře vydělte středníkem.</span><span class="sxs-lookup"><span data-stu-id="b578d-116">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b578d-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b578d-117">Child Elements</span></span>  
 <span data-ttu-id="b578d-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="b578d-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b578d-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b578d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b578d-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="b578d-120">Element</span></span>|<span data-ttu-id="b578d-121">Popis</span><span class="sxs-lookup"><span data-stu-id="b578d-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="b578d-122">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="b578d-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="b578d-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b578d-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b578d-124">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="b578d-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b578d-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="b578d-125">Example</span></span>  
 <span data-ttu-id="b578d-126">Následující příklad ukazuje, jak zadat základní podadresáře aplikace, ve které by měl modul runtime Hledat sestavení.</span><span class="sxs-lookup"><span data-stu-id="b578d-126">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b578d-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b578d-127">See also</span></span>

- [<span data-ttu-id="b578d-128">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="b578d-128">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b578d-129">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b578d-129">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b578d-130">Určení umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="b578d-130">Specifying an Assembly's Location</span></span>](../../specify-assembly-location.md)
- [<span data-ttu-id="b578d-131">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="b578d-131">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
