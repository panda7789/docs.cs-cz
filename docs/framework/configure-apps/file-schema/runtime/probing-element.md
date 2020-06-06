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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115854"
---
# <a name="probing-element"></a><span data-ttu-id="5aa20-102">Element \<probing></span><span class="sxs-lookup"><span data-stu-id="5aa20-102">\<probing> Element</span></span>
<span data-ttu-id="5aa20-103">Určuje základní podadresáře aplikace pro modul CLR (Common Language Runtime), který se má při načítání sestavení vyhledat.</span><span class="sxs-lookup"><span data-stu-id="5aa20-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<probing>**  
  
## <a name="syntax"></a><span data-ttu-id="5aa20-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5aa20-104">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5aa20-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5aa20-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5aa20-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5aa20-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5aa20-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="5aa20-107">Attributes</span></span>  
  
|<span data-ttu-id="5aa20-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="5aa20-108">Attribute</span></span>|<span data-ttu-id="5aa20-109">Popis</span><span class="sxs-lookup"><span data-stu-id="5aa20-109">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="5aa20-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="5aa20-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="5aa20-111">Určuje podadresáře základního adresáře aplikace, který může obsahovat sestavení.</span><span class="sxs-lookup"><span data-stu-id="5aa20-111">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="5aa20-112">Jednotlivé podadresáře vydělte středníkem.</span><span class="sxs-lookup"><span data-stu-id="5aa20-112">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5aa20-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5aa20-113">Child Elements</span></span>  

<span data-ttu-id="5aa20-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="5aa20-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5aa20-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5aa20-115">Parent Elements</span></span>  
  
|<span data-ttu-id="5aa20-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="5aa20-116">Element</span></span>|<span data-ttu-id="5aa20-117">Description</span><span class="sxs-lookup"><span data-stu-id="5aa20-117">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="5aa20-118">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="5aa20-118">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="5aa20-119">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5aa20-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5aa20-120">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="5aa20-120">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5aa20-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="5aa20-121">Example</span></span>  
 <span data-ttu-id="5aa20-122">Následující příklad ukazuje, jak zadat základní podadresáře aplikace, ve které by měl modul runtime Hledat sestavení.</span><span class="sxs-lookup"><span data-stu-id="5aa20-122">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5aa20-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="5aa20-123">See also</span></span>

- [<span data-ttu-id="5aa20-124">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="5aa20-124">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="5aa20-125">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="5aa20-125">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="5aa20-126">Určení umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="5aa20-126">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="5aa20-127">Způsob, jakým modul runtime vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="5aa20-127">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
