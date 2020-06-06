---
title: Element <appDomainResourceMonitoring>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: 3c6092b6c34bb13c0ad0e66df2d3b7e65ac3de7e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154373"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="477b9-102">Element \<appDomainResourceMonitoring></span><span class="sxs-lookup"><span data-stu-id="477b9-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="477b9-103">Instruuje modul runtime za účelem shromažďování statistik o všech doménách aplikace v procesu po dobu životního cyklu procesu.</span><span class="sxs-lookup"><span data-stu-id="477b9-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**  
  
## <a name="syntax"></a><span data-ttu-id="477b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="477b9-104">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="477b9-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="477b9-105">Attributes and Elements</span></span>  
 <span data-ttu-id="477b9-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="477b9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="477b9-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="477b9-107">Attributes</span></span>  
  
|<span data-ttu-id="477b9-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="477b9-108">Attribute</span></span>|<span data-ttu-id="477b9-109">Popis</span><span class="sxs-lookup"><span data-stu-id="477b9-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="477b9-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="477b9-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="477b9-111">Určuje, zda modul runtime shromažďuje statistiku pro monitorování prostředků domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="477b9-111">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="477b9-112">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="477b9-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="477b9-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="477b9-113">Value</span></span>|<span data-ttu-id="477b9-114">Description</span><span class="sxs-lookup"><span data-stu-id="477b9-114">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="477b9-115">Shromažďují se statistiky pro monitorování prostředků domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="477b9-115">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="477b9-116">Statistika pro monitorování prostředků domény aplikace se neshromažďují.</span><span class="sxs-lookup"><span data-stu-id="477b9-116">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="477b9-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="477b9-117">Child Elements</span></span>  
 <span data-ttu-id="477b9-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="477b9-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="477b9-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="477b9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="477b9-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="477b9-120">Element</span></span>|<span data-ttu-id="477b9-121">Description</span><span class="sxs-lookup"><span data-stu-id="477b9-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="477b9-122">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="477b9-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="477b9-123">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="477b9-123">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="477b9-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="477b9-124">Remarks</span></span>  
 <span data-ttu-id="477b9-125">Monitorování prostředků domény aplikace je dostupné prostřednictvím třídy domény spravované aplikace, hostitelského rozhraní [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) a trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="477b9-125">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="477b9-126">Pokud je monitorování povoleno, Statistika se shromáždí pro všechny domény aplikace v procesu po dobu životního cyklu procesu.</span><span class="sxs-lookup"><span data-stu-id="477b9-126">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="477b9-127">Chcete-li povolit monitorování ze spravovaného kódu, použijte <xref:System.AppDomain.MonitoringIsEnabled%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="477b9-127">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="477b9-128">Tento prvek konfigurace je k dispozici pouze v .NET Framework 4 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="477b9-128">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="477b9-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="477b9-129">Example</span></span>  
 <span data-ttu-id="477b9-130">Následující příklad ukazuje, jak povolit monitorování prostředků domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="477b9-130">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="477b9-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="477b9-131">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="477b9-132">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="477b9-132">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="477b9-133">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="477b9-133">Configuration File Schema</span></span>](../index.md)
