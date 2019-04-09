---
title: <developmentMode> Prvek
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdf840035150f08c894c984213af9a0abe6e95af
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192053"
---
# <a name="developmentmode-element"></a><span data-ttu-id="2eac8-102">\<developmentmode – > – Element</span><span class="sxs-lookup"><span data-stu-id="2eac8-102">\<developmentMode> Element</span></span>
<span data-ttu-id="2eac8-103">Určuje, zda modul runtime vyhledává sestavení v adresářích určených proměnnou prostředí DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="2eac8-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
 <span data-ttu-id="2eac8-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="2eac8-104">\<configuration></span></span>  
<span data-ttu-id="2eac8-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="2eac8-105">\<runtime></span></span>  
<span data-ttu-id="2eac8-106">\<developmentMode></span><span class="sxs-lookup"><span data-stu-id="2eac8-106">\<developmentMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2eac8-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2eac8-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2eac8-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2eac8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2eac8-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2eac8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2eac8-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="2eac8-110">Attributes</span></span>  
  
|<span data-ttu-id="2eac8-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="2eac8-111">Attribute</span></span>|<span data-ttu-id="2eac8-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2eac8-112">Description</span></span>|  
|---------------|-----------------|  
|**<span data-ttu-id="2eac8-113">developerInstallation</span><span class="sxs-lookup"><span data-stu-id="2eac8-113">developerInstallation</span></span>**|<span data-ttu-id="2eac8-114">Určuje, zda modul runtime vyhledává sestavení v adresářích určených proměnnou prostředí DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="2eac8-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="2eac8-115">developerInstallation atribut</span><span class="sxs-lookup"><span data-stu-id="2eac8-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="2eac8-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2eac8-116">Value</span></span>|<span data-ttu-id="2eac8-117">Popis</span><span class="sxs-lookup"><span data-stu-id="2eac8-117">Description</span></span>|  
|-----------|-----------------|  
|**<span data-ttu-id="2eac8-118">true</span><span class="sxs-lookup"><span data-stu-id="2eac8-118">true</span></span>**|<span data-ttu-id="2eac8-119">Vyhledá sestavení v adresářích určených proměnnou prostředí DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="2eac8-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|**<span data-ttu-id="2eac8-120">false</span><span class="sxs-lookup"><span data-stu-id="2eac8-120">false</span></span>**|<span data-ttu-id="2eac8-121">Není hledat sestavení v adresářích určených proměnnou prostředí DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="2eac8-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="2eac8-122">Toto je výchozí</span><span class="sxs-lookup"><span data-stu-id="2eac8-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2eac8-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2eac8-123">Child Elements</span></span>  
 <span data-ttu-id="2eac8-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="2eac8-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2eac8-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2eac8-125">Parent Elements</span></span>  
  
|<span data-ttu-id="2eac8-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="2eac8-126">Element</span></span>|<span data-ttu-id="2eac8-127">Popis</span><span class="sxs-lookup"><span data-stu-id="2eac8-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2eac8-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2eac8-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2eac8-129">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="2eac8-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2eac8-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2eac8-130">Remarks</span></span>  
 <span data-ttu-id="2eac8-131">Toto nastavení použijte jenom v době vývoje.</span><span class="sxs-lookup"><span data-stu-id="2eac8-131">Use this setting only at development time.</span></span> <span data-ttu-id="2eac8-132">Modul runtime verze sestavení se silným názvem součástí mechanismu DEVPATH nekontroluje.</span><span class="sxs-lookup"><span data-stu-id="2eac8-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="2eac8-133">Jednoduše použije první sestavení, které nalezne.</span><span class="sxs-lookup"><span data-stu-id="2eac8-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2eac8-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="2eac8-134">Example</span></span>  
 <span data-ttu-id="2eac8-135">Následující příklad ukazuje, jak mají hledat sestavení v adresářích určených proměnnou prostředí DEVPATH pomocí běhového modulu.</span><span class="sxs-lookup"><span data-stu-id="2eac8-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2eac8-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2eac8-136">See also</span></span>

- [<span data-ttu-id="2eac8-137">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="2eac8-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="2eac8-138">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="2eac8-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="2eac8-139">Postupy: Vyhledání sestavení pomocí mechanismu DEVPATH</span><span class="sxs-lookup"><span data-stu-id="2eac8-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
