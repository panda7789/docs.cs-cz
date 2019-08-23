---
title: Element <gcServer>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19ebad32ad8c7018b910a3d230f43031008dcdc7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927387"
---
# <a name="gcserver-element"></a><span data-ttu-id="71e81-102">\<gcServer – element ></span><span class="sxs-lookup"><span data-stu-id="71e81-102">\<gcServer> Element</span></span>
<span data-ttu-id="71e81-103">Určuje, zda modul CLR (Common Language Runtime) spouští uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="71e81-103">Specifies whether the common language runtime runs server garbage collection.</span></span>  
  
 <span data-ttu-id="71e81-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="71e81-104">\<configuration></span></span>  
<span data-ttu-id="71e81-105">\<> modulu runtime</span><span class="sxs-lookup"><span data-stu-id="71e81-105">\<runtime></span></span>  
<span data-ttu-id="71e81-106">\<gcServer></span><span class="sxs-lookup"><span data-stu-id="71e81-106">\<gcServer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71e81-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71e81-107">Syntax</span></span>  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71e81-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="71e81-108">Attributes and Elements</span></span>  
 <span data-ttu-id="71e81-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="71e81-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71e81-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="71e81-110">Attributes</span></span>  
  
|<span data-ttu-id="71e81-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="71e81-111">Attribute</span></span>|<span data-ttu-id="71e81-112">Popis</span><span class="sxs-lookup"><span data-stu-id="71e81-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="71e81-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="71e81-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="71e81-114">Určuje, zda modul runtime spouští uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="71e81-114">Specifies whether the runtime runs server garbage collection.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="71e81-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="71e81-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="71e81-116">Value</span><span class="sxs-lookup"><span data-stu-id="71e81-116">Value</span></span>|<span data-ttu-id="71e81-117">Popis</span><span class="sxs-lookup"><span data-stu-id="71e81-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="71e81-118">Nespustí shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="71e81-118">Does not run server garbage collection.</span></span> <span data-ttu-id="71e81-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="71e81-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="71e81-120">Spustí shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="71e81-120">Runs server garbage collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71e81-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="71e81-121">Child Elements</span></span>  
 <span data-ttu-id="71e81-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="71e81-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="71e81-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="71e81-123">Parent Elements</span></span>  
  
|<span data-ttu-id="71e81-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="71e81-124">Element</span></span>|<span data-ttu-id="71e81-125">Popis</span><span class="sxs-lookup"><span data-stu-id="71e81-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="71e81-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="71e81-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="71e81-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="71e81-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71e81-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="71e81-128">Remarks</span></span>  
 <span data-ttu-id="71e81-129">Modul CLR (Common Language Runtime) podporuje dva typy uvolňování paměti: uvolnění paměti pracovní stanice, které je k dispozici ve všech systémech a uvolňování paměti serveru, které je k dispozici v systémech s více procesory.</span><span class="sxs-lookup"><span data-stu-id="71e81-129">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="71e81-130">Pomocí `<gcServer>` elementu lze řídit typ uvolňování paměti, který modul CLR provede.</span><span class="sxs-lookup"><span data-stu-id="71e81-130">You use the `<gcServer>` element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="71e81-131"><xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> Pomocí vlastnosti určíte, zda je povoleno uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="71e81-131">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>  
  
 <span data-ttu-id="71e81-132">V případě počítačů s jedním procesorem by měla být výchozí kolekce uvolnění paměti pracovní stanice nejrychlejší možností.</span><span class="sxs-lookup"><span data-stu-id="71e81-132">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="71e81-133">Pro počítače se dvěma procesory lze použít buď pracovní stanici, nebo server.</span><span class="sxs-lookup"><span data-stu-id="71e81-133">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="71e81-134">Uvolňování paměti serveru by mělo být nejrychlejší možností pro více než dva procesory.</span><span class="sxs-lookup"><span data-stu-id="71e81-134">Server garbage collection should be the fastest option for more than two processors.</span></span>  
  
 <span data-ttu-id="71e81-135">Tento element lze použít pouze v konfiguračním souboru aplikace; ignoruje se, pokud je v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="71e81-135">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71e81-136">V .NET Framework 4 a starších verzích není souběžné uvolňování paměti k dispozici, když je povoleno uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="71e81-136">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="71e81-137">Počínaje .NET Framework 4,5 je shromažďování paměti serveru souběžné.</span><span class="sxs-lookup"><span data-stu-id="71e81-137">Starting with the .NET Framework 4.5, server garbage collection is concurrent.</span></span> <span data-ttu-id="71e81-138">Chcete-li použít nesouběžné uvolňování paměti serveru `<gcServer>` , nastavte `true` element na a [ \<gcConcurrent > element](gcconcurrent-element.md) na. `false`</span><span class="sxs-lookup"><span data-stu-id="71e81-138">To use non-concurrent server garbage collection, set the `<gcServer>` element to `true` and the [\<gcConcurrent> element](gcconcurrent-element.md) to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71e81-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="71e81-139">Example</span></span>  
 <span data-ttu-id="71e81-140">Následující příklad povoluje uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="71e81-140">The following example enables server garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="71e81-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71e81-141">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="71e81-142">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="71e81-142">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="71e81-143">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="71e81-143">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="71e81-144">Zakázání souběžného uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="71e81-144">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
