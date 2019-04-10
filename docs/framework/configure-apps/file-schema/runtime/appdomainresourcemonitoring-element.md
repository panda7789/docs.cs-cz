---
title: <appDomainResourceMonitoring> Prvek
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71cc69eba17de8465cc7999f334c724e4ec14e7d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224374"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="a6d83-102">\<appDomainResourceMonitoring> Element</span><span class="sxs-lookup"><span data-stu-id="a6d83-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="a6d83-103">Dá pokyn modulu runtime ke shromažďování statistik na všech doménách aplikace v procesu po dobu trvání procesu.</span><span class="sxs-lookup"><span data-stu-id="a6d83-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="a6d83-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="a6d83-104">\<configuration></span></span>  
<span data-ttu-id="a6d83-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="a6d83-105">\<runtime></span></span>  
<span data-ttu-id="a6d83-106">\<appDomainResourceMonitoring></span><span class="sxs-lookup"><span data-stu-id="a6d83-106">\<appDomainResourceMonitoring></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6d83-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6d83-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6d83-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a6d83-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a6d83-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a6d83-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6d83-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="a6d83-110">Attributes</span></span>  
  
|<span data-ttu-id="a6d83-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="a6d83-111">Attribute</span></span>|<span data-ttu-id="a6d83-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a6d83-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="a6d83-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="a6d83-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="a6d83-114">Určuje, zda modul runtime shromažďuje statistiky pro sledování prostředků domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="a6d83-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a6d83-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="a6d83-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="a6d83-116">Value</span><span class="sxs-lookup"><span data-stu-id="a6d83-116">Value</span></span>|<span data-ttu-id="a6d83-117">Popis</span><span class="sxs-lookup"><span data-stu-id="a6d83-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="a6d83-118">Statistika Sledování prostředků domény aplikace se shromažďují.</span><span class="sxs-lookup"><span data-stu-id="a6d83-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="a6d83-119">Statistika Sledování prostředků domény aplikace se neshromažďují.</span><span class="sxs-lookup"><span data-stu-id="a6d83-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6d83-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a6d83-120">Child Elements</span></span>  
 <span data-ttu-id="a6d83-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="a6d83-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6d83-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a6d83-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a6d83-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="a6d83-123">Element</span></span>|<span data-ttu-id="a6d83-124">Popis</span><span class="sxs-lookup"><span data-stu-id="a6d83-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a6d83-125">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a6d83-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a6d83-126">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="a6d83-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6d83-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a6d83-127">Remarks</span></span>  
 <span data-ttu-id="a6d83-128">Sledování prostředků aplikační domény nabízíme v rámci doménové třídy spravované aplikace, který je hostitelem [iclrappdomainresourcemonitor –](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) rozhraní a trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="a6d83-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="a6d83-129">Pokud je zapnuto monitorování, statistiky se shromažďují pro všechny domény aplikace v procesu po dobu trvání procesu.</span><span class="sxs-lookup"><span data-stu-id="a6d83-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="a6d83-130">Chcete-li povolit monitorování ze spravovaného kódu, použijte <xref:System.AppDomain.MonitoringIsEnabled%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a6d83-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="a6d83-131">Tento prvek konfigurace je k dispozici pouze v [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] a novější.</span><span class="sxs-lookup"><span data-stu-id="a6d83-131">This configuration element is available only in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6d83-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="a6d83-132">Example</span></span>  
 <span data-ttu-id="a6d83-133">Následující příklad ukazuje, jak povolit sledování prostředků domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="a6d83-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6d83-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6d83-134">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a6d83-135">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="a6d83-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="a6d83-136">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="a6d83-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
