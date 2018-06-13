---
title: '&lt;developmentmode –&gt; – Element'
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
ms.openlocfilehash: 71b4eb1dfb50774cea2f7a50d5e5350b0338f41e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745497"
---
# <a name="ltdevelopmentmodegt-element"></a><span data-ttu-id="431b3-102">&lt;developmentmode –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="431b3-102">&lt;developmentMode&gt; Element</span></span>
<span data-ttu-id="431b3-103">Určuje, zda běhové prostředí vyhledává sestavení v zadaném proměnnou prostředí DEVPATH adresáře.</span><span class="sxs-lookup"><span data-stu-id="431b3-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
 <span data-ttu-id="431b3-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="431b3-104">\<configuration></span></span>  
<span data-ttu-id="431b3-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="431b3-105">\<runtime></span></span>  
<span data-ttu-id="431b3-106">\<developmentmode – ></span><span class="sxs-lookup"><span data-stu-id="431b3-106">\<developmentMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="431b3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="431b3-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="431b3-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="431b3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="431b3-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="431b3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="431b3-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="431b3-110">Attributes</span></span>  
  
|<span data-ttu-id="431b3-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="431b3-111">Attribute</span></span>|<span data-ttu-id="431b3-112">Popis</span><span class="sxs-lookup"><span data-stu-id="431b3-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="431b3-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="431b3-113">**developerInstallation**</span></span>|<span data-ttu-id="431b3-114">Určuje, zda běhové prostředí vyhledává sestavení v zadaném proměnnou prostředí DEVPATH adresáře.</span><span class="sxs-lookup"><span data-stu-id="431b3-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="431b3-115">developerInstallation atribut</span><span class="sxs-lookup"><span data-stu-id="431b3-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="431b3-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="431b3-116">Value</span></span>|<span data-ttu-id="431b3-117">Popis</span><span class="sxs-lookup"><span data-stu-id="431b3-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="431b3-118">**true**</span><span class="sxs-lookup"><span data-stu-id="431b3-118">**true**</span></span>|<span data-ttu-id="431b3-119">Vyhledá sestavení v zadaném proměnnou prostředí DEVPATH adresáře.</span><span class="sxs-lookup"><span data-stu-id="431b3-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="431b3-120">**false**</span><span class="sxs-lookup"><span data-stu-id="431b3-120">**false**</span></span>|<span data-ttu-id="431b3-121">Nehledá sestavení v zadaném proměnnou prostředí DEVPATH adresáře.</span><span class="sxs-lookup"><span data-stu-id="431b3-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="431b3-122">Toto je výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="431b3-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="431b3-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="431b3-123">Child Elements</span></span>  
 <span data-ttu-id="431b3-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="431b3-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="431b3-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="431b3-125">Parent Elements</span></span>  
  
|<span data-ttu-id="431b3-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="431b3-126">Element</span></span>|<span data-ttu-id="431b3-127">Popis</span><span class="sxs-lookup"><span data-stu-id="431b3-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="431b3-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="431b3-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="431b3-129">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="431b3-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="431b3-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="431b3-130">Remarks</span></span>  
 <span data-ttu-id="431b3-131">Toto nastavení používejte pouze v době vývoj.</span><span class="sxs-lookup"><span data-stu-id="431b3-131">Use this setting only at development time.</span></span> <span data-ttu-id="431b3-132">Modul runtime nekontroluje verze na sestavení se silným názvem v mechanismu DEVPATH nalezen.</span><span class="sxs-lookup"><span data-stu-id="431b3-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="431b3-133">Jednoduše použije první sestavení, které najde.</span><span class="sxs-lookup"><span data-stu-id="431b3-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="431b3-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="431b3-134">Example</span></span>  
 <span data-ttu-id="431b3-135">Následující příklad ukazuje, jak způsobí modulu runtime pro vyhledání sestavení v zadaném proměnnou prostředí DEVPATH adresáře.</span><span class="sxs-lookup"><span data-stu-id="431b3-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="431b3-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="431b3-136">See Also</span></span>  
 [<span data-ttu-id="431b3-137">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="431b3-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="431b3-138">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="431b3-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="431b3-139">Postupy: Vyhledání sestavení pomocí mechanismu DEVPATH</span><span class="sxs-lookup"><span data-stu-id="431b3-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
