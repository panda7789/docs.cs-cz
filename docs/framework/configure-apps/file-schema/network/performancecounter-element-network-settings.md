---
title: <performanceCounter> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: 4603a942788d31a049196fb699d07a13551fa443
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279757"
---
# <a name="performancecounter-element-network-settings"></a><span data-ttu-id="4afd7-102">\<performanceCounter > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="4afd7-102">\<performanceCounter> Element (Network Settings)</span></span>
<span data-ttu-id="4afd7-103">Povolí nebo zakáže čítače výkonu sítě.</span><span class="sxs-lookup"><span data-stu-id="4afd7-103">Enables or disables networking performance counters.</span></span>  
  
 <span data-ttu-id="4afd7-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="4afd7-104">\<configuration></span></span>  
<span data-ttu-id="4afd7-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="4afd7-105">\<system.net></span></span>  
<span data-ttu-id="4afd7-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="4afd7-106">\<settings></span></span>  
<span data-ttu-id="4afd7-107">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="4afd7-107">\<performanceCounters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4afd7-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4afd7-108">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4afd7-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4afd7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4afd7-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4afd7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4afd7-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="4afd7-111">Attributes</span></span>  
  
|<span data-ttu-id="4afd7-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="4afd7-112">Attribute</span></span>|<span data-ttu-id="4afd7-113">Popis</span><span class="sxs-lookup"><span data-stu-id="4afd7-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="4afd7-114">Určuje, zda jsou povoleny čítače výkonu sítě.</span><span class="sxs-lookup"><span data-stu-id="4afd7-114">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="4afd7-115">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="4afd7-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4afd7-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4afd7-116">Child Elements</span></span>  
 <span data-ttu-id="4afd7-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="4afd7-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4afd7-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4afd7-118">Parent Elements</span></span>  
  
|<span data-ttu-id="4afd7-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="4afd7-119">Element</span></span>|<span data-ttu-id="4afd7-120">Popis</span><span class="sxs-lookup"><span data-stu-id="4afd7-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4afd7-121">settings</span><span class="sxs-lookup"><span data-stu-id="4afd7-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="4afd7-122">Nakonfiguruje možnosti základní sítě pro <xref:System.Net> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4afd7-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4afd7-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4afd7-123">Remarks</span></span>  
 <span data-ttu-id="4afd7-124">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="4afd7-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="4afd7-125">Čítače výkonu sítě musí být povolené v konfiguračním souboru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="4afd7-125">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="4afd7-126">Všechny čítače výkonu sítě jsou povolené nebo zakázané s jedno nastavení v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="4afd7-126">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="4afd7-127">Jednotlivé čítače výkonu sítě nemůže být povolena nebo zakázána.</span><span class="sxs-lookup"><span data-stu-id="4afd7-127">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="4afd7-128">Další informace o konkrétní čítače výkonu sítě, naleznete v tématu [čítače výkonu sítě](../../../../../docs/framework/debug-trace-profile/performance-counters.md#networking).</span><span class="sxs-lookup"><span data-stu-id="4afd7-128">For more information on the specific networking performance counters, see [Networking Performance Counters](../../../../../docs/framework/debug-trace-profile/performance-counters.md#networking).</span></span>  
  
 <span data-ttu-id="4afd7-129">Výchozí hodnota je tento výkon sítě za čítače jsou zakázané.</span><span class="sxs-lookup"><span data-stu-id="4afd7-129">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="4afd7-130"><xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnoty **povolené** atribut z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="4afd7-130">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4afd7-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="4afd7-131">Example</span></span>  
 <span data-ttu-id="4afd7-132">Následující příklad ukazuje, jak nakonfigurovat <xref:System.Net> a souvisejících oborech názvů umožňuje čítače výkonu sítě.</span><span class="sxs-lookup"><span data-stu-id="4afd7-132">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <performanceCounters  
        enabled="true"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4afd7-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4afd7-133">See also</span></span>
- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4afd7-134">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="4afd7-134">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="4afd7-135">Čítače výkonu sítě</span><span class="sxs-lookup"><span data-stu-id="4afd7-135">Networking Performance Counters</span></span>](../../../../../docs/framework/debug-trace-profile/performance-counters.md#networking)
