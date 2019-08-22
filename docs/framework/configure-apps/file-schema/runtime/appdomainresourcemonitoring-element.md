---
title: Element <appDomainResourceMonitoring>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b82be30c18cde361aa412ee1b631c8368c8de1b3
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663932"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="82744-102">\<appDomainResourceMonitoring> Element</span><span class="sxs-lookup"><span data-stu-id="82744-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="82744-103">Instruuje modul runtime za účelem shromažďování statistik o všech doménách aplikace v procesu po dobu životního cyklu procesu.</span><span class="sxs-lookup"><span data-stu-id="82744-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="82744-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="82744-104">\<configuration></span></span>  
<span data-ttu-id="82744-105">\<> modulu runtime</span><span class="sxs-lookup"><span data-stu-id="82744-105">\<runtime></span></span>  
<span data-ttu-id="82744-106">\<appDomainResourceMonitoring></span><span class="sxs-lookup"><span data-stu-id="82744-106">\<appDomainResourceMonitoring></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82744-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82744-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82744-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="82744-108">Attributes and Elements</span></span>  
 <span data-ttu-id="82744-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="82744-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82744-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="82744-110">Attributes</span></span>  
  
|<span data-ttu-id="82744-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="82744-111">Attribute</span></span>|<span data-ttu-id="82744-112">Popis</span><span class="sxs-lookup"><span data-stu-id="82744-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="82744-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="82744-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="82744-114">Určuje, zda modul runtime shromažďuje statistiku pro monitorování prostředků domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="82744-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="82744-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="82744-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="82744-116">Value</span><span class="sxs-lookup"><span data-stu-id="82744-116">Value</span></span>|<span data-ttu-id="82744-117">Popis</span><span class="sxs-lookup"><span data-stu-id="82744-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="82744-118">Shromažďují se statistiky pro monitorování prostředků domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="82744-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="82744-119">Statistika pro monitorování prostředků domény aplikace se neshromažďují.</span><span class="sxs-lookup"><span data-stu-id="82744-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82744-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="82744-120">Child Elements</span></span>  
 <span data-ttu-id="82744-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="82744-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="82744-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="82744-122">Parent Elements</span></span>  
  
|<span data-ttu-id="82744-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="82744-123">Element</span></span>|<span data-ttu-id="82744-124">Popis</span><span class="sxs-lookup"><span data-stu-id="82744-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="82744-125">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="82744-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="82744-126">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="82744-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82744-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="82744-127">Remarks</span></span>  
 <span data-ttu-id="82744-128">Monitorování prostředků domény aplikace je dostupné prostřednictvím třídy domény spravované aplikace, hostitelského rozhraní [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) a trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="82744-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="82744-129">Pokud je monitorování povoleno, Statistika se shromáždí pro všechny domény aplikace v procesu po dobu životního cyklu procesu.</span><span class="sxs-lookup"><span data-stu-id="82744-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="82744-130">Chcete-li povolit monitorování ze spravovaného kódu <xref:System.AppDomain.MonitoringIsEnabled%2A> , použijte vlastnost.</span><span class="sxs-lookup"><span data-stu-id="82744-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="82744-131">Tento prvek konfigurace je k dispozici pouze v .NET Framework 4 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="82744-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82744-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="82744-132">Example</span></span>  
 <span data-ttu-id="82744-133">Následující příklad ukazuje, jak povolit monitorování prostředků domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="82744-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="82744-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82744-134">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="82744-135">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="82744-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="82744-136">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="82744-136">Configuration File Schema</span></span>](../index.md)
