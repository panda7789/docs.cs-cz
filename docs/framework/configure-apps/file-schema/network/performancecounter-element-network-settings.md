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
ms.openlocfilehash: 58a2bf5118a3a2cd9c33301eca5dcc751c2351bf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283083"
---
# <a name="performancecounter-element-network-settings"></a><span data-ttu-id="c6dc6-102">\<element > performanceCounter (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="c6dc6-102">\<performanceCounter> Element (Network Settings)</span></span>
<span data-ttu-id="c6dc6-103">Povolí nebo zakáže čítače výkonu sítě.</span><span class="sxs-lookup"><span data-stu-id="c6dc6-103">Enables or disables networking performance counters.</span></span>  

<span data-ttu-id="c6dc6-104">[**konfigurační >\<** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c6dc6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c6dc6-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c6dc6-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="c6dc6-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<nastavení >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c6dc6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>\
<span data-ttu-id="c6dc6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<čítače výkonu >**</span><span class="sxs-lookup"><span data-stu-id="c6dc6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c6dc6-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6dc6-108">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6dc6-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c6dc6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c6dc6-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c6dc6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6dc6-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="c6dc6-111">Attributes</span></span>  
  
|<span data-ttu-id="c6dc6-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="c6dc6-112">Attribute</span></span>|<span data-ttu-id="c6dc6-113">Popis</span><span class="sxs-lookup"><span data-stu-id="c6dc6-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="c6dc6-114">Určuje, zda jsou povoleny čítače výkonu sítě.</span><span class="sxs-lookup"><span data-stu-id="c6dc6-114">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="c6dc6-115">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="c6dc6-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6dc6-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c6dc6-116">Child Elements</span></span>  
 <span data-ttu-id="c6dc6-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="c6dc6-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c6dc6-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c6dc6-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c6dc6-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="c6dc6-119">Element</span></span>|<span data-ttu-id="c6dc6-120">Popis</span><span class="sxs-lookup"><span data-stu-id="c6dc6-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6dc6-121">možnost</span><span class="sxs-lookup"><span data-stu-id="c6dc6-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="c6dc6-122">Konfiguruje základní možnosti sítě pro obor názvů <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="c6dc6-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6dc6-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6dc6-123">Remarks</span></span>  
 <span data-ttu-id="c6dc6-124">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="c6dc6-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="c6dc6-125">V konfiguračním souboru musí být povolené čítače výkonu sítě, které se mají použít.</span><span class="sxs-lookup"><span data-stu-id="c6dc6-125">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="c6dc6-126">Všechny čítače výkonu sítě jsou povoleny nebo zakázány v jednom nastavení konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="c6dc6-126">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="c6dc6-127">Nelze povolit nebo zakázat jednotlivé čítače výkonu sítě.</span><span class="sxs-lookup"><span data-stu-id="c6dc6-127">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="c6dc6-128">Další informace o konkrétních čítačích výkonu sítě najdete v tématu [čítače výkonu sítě](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span><span class="sxs-lookup"><span data-stu-id="c6dc6-128">For more information on the specific networking performance counters, see [Networking performance counters](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span></span>  
  
 <span data-ttu-id="c6dc6-129">Výchozí hodnota je zakázané čítače výkonu sítě.</span><span class="sxs-lookup"><span data-stu-id="c6dc6-129">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="c6dc6-130">Vlastnost <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> lze použít k získání aktuální hodnoty atributu **Enabled** z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="c6dc6-130">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6dc6-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6dc6-131">Example</span></span>  
 <span data-ttu-id="c6dc6-132">Následující příklad ukazuje, jak nakonfigurovat <xref:System.Net> a související obory názvů pro povolení čítačů výkonu sítě.</span><span class="sxs-lookup"><span data-stu-id="c6dc6-132">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c6dc6-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6dc6-133">See also</span></span>

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c6dc6-134">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="c6dc6-134">Network Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c6dc6-135">Čítače výkonu sítě</span><span class="sxs-lookup"><span data-stu-id="c6dc6-135">Networking Performance Counters</span></span>](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)
