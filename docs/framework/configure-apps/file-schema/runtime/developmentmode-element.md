---
title: Element <developmentMode>
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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59192053"
---
# <a name="developmentmode-element"></a><span data-ttu-id="28e3f-102">\<developmentmode – > – Element</span><span class="sxs-lookup"><span data-stu-id="28e3f-102">\<developmentMode> Element</span></span>
<span data-ttu-id="28e3f-103">Určuje, zda modul runtime vyhledává sestavení v adresářích určených proměnnou prostředí DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="28e3f-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
 <span data-ttu-id="28e3f-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="28e3f-104">\<configuration></span></span>  
<span data-ttu-id="28e3f-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="28e3f-105">\<runtime></span></span>  
<span data-ttu-id="28e3f-106">\<developmentMode></span><span class="sxs-lookup"><span data-stu-id="28e3f-106">\<developmentMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28e3f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28e3f-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28e3f-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="28e3f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="28e3f-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="28e3f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28e3f-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="28e3f-110">Attributes</span></span>  
  
|<span data-ttu-id="28e3f-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="28e3f-111">Attribute</span></span>|<span data-ttu-id="28e3f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="28e3f-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="28e3f-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="28e3f-113">**developerInstallation**</span></span>|<span data-ttu-id="28e3f-114">Určuje, zda modul runtime vyhledává sestavení v adresářích určených proměnnou prostředí DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="28e3f-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="28e3f-115">developerInstallation atribut</span><span class="sxs-lookup"><span data-stu-id="28e3f-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="28e3f-116">Value</span><span class="sxs-lookup"><span data-stu-id="28e3f-116">Value</span></span>|<span data-ttu-id="28e3f-117">Popis</span><span class="sxs-lookup"><span data-stu-id="28e3f-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="28e3f-118">**true**</span><span class="sxs-lookup"><span data-stu-id="28e3f-118">**true**</span></span>|<span data-ttu-id="28e3f-119">Vyhledá sestavení v adresářích určených proměnnou prostředí DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="28e3f-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="28e3f-120">**false**</span><span class="sxs-lookup"><span data-stu-id="28e3f-120">**false**</span></span>|<span data-ttu-id="28e3f-121">Není hledat sestavení v adresářích určených proměnnou prostředí DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="28e3f-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="28e3f-122">Toto je výchozí</span><span class="sxs-lookup"><span data-stu-id="28e3f-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28e3f-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="28e3f-123">Child Elements</span></span>  
 <span data-ttu-id="28e3f-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="28e3f-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="28e3f-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="28e3f-125">Parent Elements</span></span>  
  
|<span data-ttu-id="28e3f-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="28e3f-126">Element</span></span>|<span data-ttu-id="28e3f-127">Popis</span><span class="sxs-lookup"><span data-stu-id="28e3f-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="28e3f-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="28e3f-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="28e3f-129">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="28e3f-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28e3f-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="28e3f-130">Remarks</span></span>  
 <span data-ttu-id="28e3f-131">Toto nastavení použijte jenom v době vývoje.</span><span class="sxs-lookup"><span data-stu-id="28e3f-131">Use this setting only at development time.</span></span> <span data-ttu-id="28e3f-132">Modul runtime verze sestavení se silným názvem součástí mechanismu DEVPATH nekontroluje.</span><span class="sxs-lookup"><span data-stu-id="28e3f-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="28e3f-133">Jednoduše použije první sestavení, které nalezne.</span><span class="sxs-lookup"><span data-stu-id="28e3f-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28e3f-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="28e3f-134">Example</span></span>  
 <span data-ttu-id="28e3f-135">Následující příklad ukazuje, jak mají hledat sestavení v adresářích určených proměnnou prostředí DEVPATH pomocí běhového modulu.</span><span class="sxs-lookup"><span data-stu-id="28e3f-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="28e3f-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="28e3f-136">See also</span></span>

- [<span data-ttu-id="28e3f-137">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="28e3f-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="28e3f-138">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="28e3f-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="28e3f-139">Postupy: Vyhledání sestavení pomocí mechanismu DEVPATH</span><span class="sxs-lookup"><span data-stu-id="28e3f-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
