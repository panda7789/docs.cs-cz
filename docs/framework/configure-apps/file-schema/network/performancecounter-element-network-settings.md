---
title: '&lt;performanceCounter&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5879614fd34fe645899f1b95f41e9b0675418292
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltperformancecountergt-element-network-settings"></a><span data-ttu-id="bfaaf-102">&lt;performanceCounter&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="bfaaf-102">&lt;performanceCounter&gt; Element (Network Settings)</span></span>
<span data-ttu-id="bfaaf-103">Povolí nebo zakáže sítě čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="bfaaf-103">Enables or disables networking performance counters.</span></span>  
  
 <span data-ttu-id="bfaaf-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="bfaaf-104">\<configuration></span></span>  
<span data-ttu-id="bfaaf-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="bfaaf-105">\<system.net></span></span>  
<span data-ttu-id="bfaaf-106">\<Nastavení ></span><span class="sxs-lookup"><span data-stu-id="bfaaf-106">\<settings></span></span>  
<span data-ttu-id="bfaaf-107">\<čítače výkonu ></span><span class="sxs-lookup"><span data-stu-id="bfaaf-107">\<performanceCounters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfaaf-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bfaaf-108">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bfaaf-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bfaaf-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bfaaf-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bfaaf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bfaaf-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="bfaaf-111">Attributes</span></span>  
  
|<span data-ttu-id="bfaaf-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="bfaaf-112">Attribute</span></span>|<span data-ttu-id="bfaaf-113">Popis</span><span class="sxs-lookup"><span data-stu-id="bfaaf-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="bfaaf-114">Určuje, zda jsou povoleny čítače výkonu sítě.</span><span class="sxs-lookup"><span data-stu-id="bfaaf-114">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="bfaaf-115">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="bfaaf-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bfaaf-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bfaaf-116">Child Elements</span></span>  
 <span data-ttu-id="bfaaf-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="bfaaf-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bfaaf-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bfaaf-118">Parent Elements</span></span>  
  
|<span data-ttu-id="bfaaf-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="bfaaf-119">Element</span></span>|<span data-ttu-id="bfaaf-120">Popis</span><span class="sxs-lookup"><span data-stu-id="bfaaf-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bfaaf-121">Nastavení</span><span class="sxs-lookup"><span data-stu-id="bfaaf-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="bfaaf-122">Nakonfiguruje možnosti základní sítě <xref:System.Net> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="bfaaf-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfaaf-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bfaaf-123">Remarks</span></span>  
 <span data-ttu-id="bfaaf-124">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="bfaaf-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="bfaaf-125">Čítače výkonu sítě je nutné povolit v konfiguračním souboru má být použit.</span><span class="sxs-lookup"><span data-stu-id="bfaaf-125">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="bfaaf-126">Všechny síťové čítače výkonu jsou zapnutá nebo vypnutá s jedním nastavením v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="bfaaf-126">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="bfaaf-127">Nelze povolit nebo zakázat jednotlivé čítače výkonu sítě.</span><span class="sxs-lookup"><span data-stu-id="bfaaf-127">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="bfaaf-128">Další informace o konkrétní síťové čítače výkonu, najdete v části [sítě čítače výkonu](http://msdn.microsoft.com/library/d1860235-f643-46ae-846c-ff0ed8b0e3cd).</span><span class="sxs-lookup"><span data-stu-id="bfaaf-128">For more information on the specific networking performance counters, see [Networking Performance Counters](http://msdn.microsoft.com/library/d1860235-f643-46ae-846c-ff0ed8b0e3cd).</span></span>  
  
 <span data-ttu-id="bfaaf-129">Výchozí hodnota je tento výkon sítě, které čítače jsou zakázány.</span><span class="sxs-lookup"><span data-stu-id="bfaaf-129">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="bfaaf-130"><xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnota **povoleno** atribut z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="bfaaf-130">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfaaf-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="bfaaf-131">Example</span></span>  
 <span data-ttu-id="bfaaf-132">Následující příklad ukazuje, jak nakonfigurovat <xref:System.Net> a související obory názvů povolit sítě čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="bfaaf-132">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bfaaf-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="bfaaf-133">See Also</span></span>  
 <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="bfaaf-134">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="bfaaf-134">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [<span data-ttu-id="bfaaf-135">Čítače výkonu sítě</span><span class="sxs-lookup"><span data-stu-id="bfaaf-135">Networking Performance Counters</span></span>](http://msdn.microsoft.com/library/d1860235-f643-46ae-846c-ff0ed8b0e3cd)
