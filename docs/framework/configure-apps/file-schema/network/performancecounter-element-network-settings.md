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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74283083"
---
# <a name="performancecounter-element-network-settings"></a><span data-ttu-id="b4984-102">\<performanceCounter> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="b4984-102">\<performanceCounter> Element (Network Settings)</span></span>
<span data-ttu-id="b4984-103">Povolí nebo zakáže čítače výkonu sítě.</span><span class="sxs-lookup"><span data-stu-id="b4984-103">Enables or disables networking performance counters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**

## <a name="syntax"></a><span data-ttu-id="b4984-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4984-104">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4984-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b4984-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b4984-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b4984-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4984-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="b4984-107">Attributes</span></span>  
  
|<span data-ttu-id="b4984-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="b4984-108">Attribute</span></span>|<span data-ttu-id="b4984-109">Popis</span><span class="sxs-lookup"><span data-stu-id="b4984-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="b4984-110">Určuje, zda jsou povoleny čítače výkonu sítě.</span><span class="sxs-lookup"><span data-stu-id="b4984-110">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="b4984-111">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="b4984-111">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b4984-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b4984-112">Child Elements</span></span>  
 <span data-ttu-id="b4984-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="b4984-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b4984-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b4984-114">Parent Elements</span></span>  
  
|<span data-ttu-id="b4984-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="b4984-115">Element</span></span>|<span data-ttu-id="b4984-116">Description</span><span class="sxs-lookup"><span data-stu-id="b4984-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4984-117">zdroje dat</span><span class="sxs-lookup"><span data-stu-id="b4984-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="b4984-118">Nakonfiguruje základní možnosti sítě pro <xref:System.Net> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="b4984-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4984-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4984-119">Remarks</span></span>  
 <span data-ttu-id="b4984-120">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="b4984-120">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="b4984-121">V konfiguračním souboru musí být povolené čítače výkonu sítě, které se mají použít.</span><span class="sxs-lookup"><span data-stu-id="b4984-121">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="b4984-122">Všechny čítače výkonu sítě jsou povoleny nebo zakázány v jednom nastavení konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="b4984-122">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="b4984-123">Nelze povolit nebo zakázat jednotlivé čítače výkonu sítě.</span><span class="sxs-lookup"><span data-stu-id="b4984-123">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="b4984-124">Další informace o konkrétních čítačích výkonu sítě najdete v tématu [čítače výkonu sítě](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span><span class="sxs-lookup"><span data-stu-id="b4984-124">For more information on the specific networking performance counters, see [Networking performance counters](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span></span>  
  
 <span data-ttu-id="b4984-125">Výchozí hodnota je zakázané čítače výkonu sítě.</span><span class="sxs-lookup"><span data-stu-id="b4984-125">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="b4984-126"><xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>Vlastnost lze použít k získání aktuální hodnoty atributu **Enabled** z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="b4984-126">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4984-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="b4984-127">Example</span></span>  
 <span data-ttu-id="b4984-128">Následující příklad ukazuje, jak nakonfigurovat <xref:System.Net> a související obory názvů pro povolení čítačů výkonu sítě.</span><span class="sxs-lookup"><span data-stu-id="b4984-128">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b4984-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4984-129">See also</span></span>

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b4984-130">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="b4984-130">Network Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b4984-131">Čítače výkonu sítě</span><span class="sxs-lookup"><span data-stu-id="b4984-131">Networking Performance Counters</span></span>](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)
