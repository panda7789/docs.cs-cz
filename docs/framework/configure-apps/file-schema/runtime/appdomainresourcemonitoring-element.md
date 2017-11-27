---
title: "&lt;appdomainresourcemonitoring –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5c9591789c007466adce107732a7ab777b1de241
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltappdomainresourcemonitoringgt-element"></a><span data-ttu-id="2fbc0-102">&lt;appdomainresourcemonitoring –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="2fbc0-102">&lt;appDomainResourceMonitoring&gt; Element</span></span>
<span data-ttu-id="2fbc0-103">Dá pokyn modulu runtime ke shromažďování statistik na všechny domény aplikace v procesu po dobu trvání procesu.</span><span class="sxs-lookup"><span data-stu-id="2fbc0-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="2fbc0-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="2fbc0-104">\<configuration></span></span>  
<span data-ttu-id="2fbc0-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="2fbc0-105">\<runtime></span></span>  
<span data-ttu-id="2fbc0-106">\<appdomainresourcemonitoring – ></span><span class="sxs-lookup"><span data-stu-id="2fbc0-106">\<appDomainResourceMonitoring></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fbc0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fbc0-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2fbc0-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2fbc0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2fbc0-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2fbc0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2fbc0-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="2fbc0-110">Attributes</span></span>  
  
|<span data-ttu-id="2fbc0-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="2fbc0-111">Attribute</span></span>|<span data-ttu-id="2fbc0-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2fbc0-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="2fbc0-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="2fbc0-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="2fbc0-114">Určuje, zda modul runtime shromažďuje statistiky pro sledování prostředků domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="2fbc0-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="2fbc0-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="2fbc0-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="2fbc0-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2fbc0-116">Value</span></span>|<span data-ttu-id="2fbc0-117">Popis</span><span class="sxs-lookup"><span data-stu-id="2fbc0-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="2fbc0-118">Statistiky pro sledování prostředků domény aplikace se shromažďují.</span><span class="sxs-lookup"><span data-stu-id="2fbc0-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="2fbc0-119">Statistiky pro sledování prostředků domény aplikace nejsou shromážděna.</span><span class="sxs-lookup"><span data-stu-id="2fbc0-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2fbc0-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2fbc0-120">Child Elements</span></span>  
 <span data-ttu-id="2fbc0-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="2fbc0-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2fbc0-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2fbc0-122">Parent Elements</span></span>  
  
|<span data-ttu-id="2fbc0-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="2fbc0-123">Element</span></span>|<span data-ttu-id="2fbc0-124">Popis</span><span class="sxs-lookup"><span data-stu-id="2fbc0-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2fbc0-125">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2fbc0-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2fbc0-126">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="2fbc0-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2fbc0-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2fbc0-127">Remarks</span></span>  
 <span data-ttu-id="2fbc0-128">Sledování prostředků domény aplikace je k dispozici prostřednictvím třídy domény spravované aplikace, který je hostitelem [iclrappdomainresourcemonitor –](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) rozhraní a trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="2fbc0-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="2fbc0-129">Pokud je zapnuto monitorování, statistiky se shromažďují pro všechny domény aplikace v procesu po dobu trvání procesu.</span><span class="sxs-lookup"><span data-stu-id="2fbc0-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="2fbc0-130">Chcete-li monitorování povolit ze spravovaného kódu, použijte <xref:System.AppDomain.MonitoringIsEnabled%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2fbc0-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="2fbc0-131">Tento element konfigurace je k dispozici pouze v [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] a novější.</span><span class="sxs-lookup"><span data-stu-id="2fbc0-131">This configuration element is available only in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fbc0-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="2fbc0-132">Example</span></span>  
 <span data-ttu-id="2fbc0-133">Následující příklad ukazuje, jak povolit sledování prostředků domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="2fbc0-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2fbc0-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="2fbc0-134">See Also</span></span>  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="2fbc0-135">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="2fbc0-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="2fbc0-136">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="2fbc0-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
