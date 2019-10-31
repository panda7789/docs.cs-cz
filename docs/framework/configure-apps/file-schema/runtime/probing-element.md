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
ms.openlocfilehash: e9e48ea97e1b70fef7fcc78a113e18c5fec23b7c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115854"
---
# <a name="probing-element"></a><span data-ttu-id="aad44-102">\<> elementu zjišťování</span><span class="sxs-lookup"><span data-stu-id="aad44-102">\<probing> Element</span></span>
<span data-ttu-id="aad44-103">Určuje základní podadresáře aplikace pro modul CLR (Common Language Runtime), který se má při načítání sestavení vyhledat.</span><span class="sxs-lookup"><span data-stu-id="aad44-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
<span data-ttu-id="aad44-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="aad44-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="aad44-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="aad44-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="aad44-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="aad44-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="aad44-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zjišťování >**</span><span class="sxs-lookup"><span data-stu-id="aad44-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<probing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aad44-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aad44-108">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aad44-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="aad44-109">Attributes and Elements</span></span>  
 <span data-ttu-id="aad44-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="aad44-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aad44-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="aad44-111">Attributes</span></span>  
  
|<span data-ttu-id="aad44-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="aad44-112">Attribute</span></span>|<span data-ttu-id="aad44-113">Popis</span><span class="sxs-lookup"><span data-stu-id="aad44-113">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="aad44-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="aad44-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="aad44-115">Určuje podadresáře základního adresáře aplikace, který může obsahovat sestavení.</span><span class="sxs-lookup"><span data-stu-id="aad44-115">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="aad44-116">Jednotlivé podadresáře vydělte středníkem.</span><span class="sxs-lookup"><span data-stu-id="aad44-116">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aad44-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="aad44-117">Child Elements</span></span>  

<span data-ttu-id="aad44-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="aad44-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aad44-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="aad44-119">Parent Elements</span></span>  
  
|<span data-ttu-id="aad44-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="aad44-120">Element</span></span>|<span data-ttu-id="aad44-121">Popis</span><span class="sxs-lookup"><span data-stu-id="aad44-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="aad44-122">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="aad44-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="aad44-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aad44-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="aad44-124">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="aad44-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="aad44-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="aad44-125">Example</span></span>  
 <span data-ttu-id="aad44-126">Následující příklad ukazuje, jak zadat základní podadresáře aplikace, ve které by měl modul runtime Hledat sestavení.</span><span class="sxs-lookup"><span data-stu-id="aad44-126">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aad44-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aad44-127">See also</span></span>

- [<span data-ttu-id="aad44-128">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="aad44-128">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="aad44-129">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="aad44-129">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="aad44-130">Určení umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="aad44-130">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="aad44-131">Způsob, jakým modul runtime vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="aad44-131">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
