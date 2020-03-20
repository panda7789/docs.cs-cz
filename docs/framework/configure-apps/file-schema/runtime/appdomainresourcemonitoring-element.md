---
title: Element <appDomainResourceMonitoring>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: 3c6092b6c34bb13c0ad0e66df2d3b7e65ac3de7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154373"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="d36b2-102">\<appDomainResourceMonitoring> element</span><span class="sxs-lookup"><span data-stu-id="d36b2-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="d36b2-103">Dává pokyn běhu shromažďovat statistiky o všech aplikačních doménv procesu po dobu životnosti procesu.</span><span class="sxs-lookup"><span data-stu-id="d36b2-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
<span data-ttu-id="d36b2-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d36b2-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d36b2-105">&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="d36b2-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="d36b2-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**</span><span class="sxs-lookup"><span data-stu-id="d36b2-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d36b2-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d36b2-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d36b2-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d36b2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d36b2-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d36b2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d36b2-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="d36b2-110">Attributes</span></span>  
  
|<span data-ttu-id="d36b2-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="d36b2-111">Attribute</span></span>|<span data-ttu-id="d36b2-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d36b2-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d36b2-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="d36b2-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d36b2-114">Určuje, zda program runtime shromažďuje statistiky pro monitorování prostředků domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="d36b2-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d36b2-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="d36b2-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d36b2-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d36b2-116">Value</span></span>|<span data-ttu-id="d36b2-117">Popis</span><span class="sxs-lookup"><span data-stu-id="d36b2-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="d36b2-118">Jsou shromažďovány statistiky pro monitorování prostředků domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="d36b2-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="d36b2-119">Statistiky pro monitorování prostředků domény aplikace nejsou shromažďovány.</span><span class="sxs-lookup"><span data-stu-id="d36b2-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d36b2-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d36b2-120">Child Elements</span></span>  
 <span data-ttu-id="d36b2-121">Žádné.</span><span class="sxs-lookup"><span data-stu-id="d36b2-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d36b2-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d36b2-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d36b2-123">Element</span><span class="sxs-lookup"><span data-stu-id="d36b2-123">Element</span></span>|<span data-ttu-id="d36b2-124">Popis</span><span class="sxs-lookup"><span data-stu-id="d36b2-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d36b2-125">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d36b2-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d36b2-126">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d36b2-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d36b2-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d36b2-127">Remarks</span></span>  
 <span data-ttu-id="d36b2-128">Monitorování prostředků domény aplikace je k dispozici prostřednictvím třídy domény spravované aplikace, hostitelského rozhraní [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) a trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="d36b2-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="d36b2-129">Pokud je povoleno monitorování, statistiky jsou shromažďovány pro všechny aplikační domény v procesu po dobu životnosti procesu.</span><span class="sxs-lookup"><span data-stu-id="d36b2-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="d36b2-130">Chcete-li povolit monitorování <xref:System.AppDomain.MonitoringIsEnabled%2A> ze spravovaného kódu, použijte vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d36b2-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="d36b2-131">Tento konfigurační prvek je k dispozici pouze v rozhraní .NET Framework 4 a novější.</span><span class="sxs-lookup"><span data-stu-id="d36b2-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d36b2-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="d36b2-132">Example</span></span>  
 <span data-ttu-id="d36b2-133">Následující příklad ukazuje, jak povolit monitorování prostředků domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="d36b2-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d36b2-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="d36b2-134">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d36b2-135">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="d36b2-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d36b2-136">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="d36b2-136">Configuration File Schema</span></span>](../index.md)
