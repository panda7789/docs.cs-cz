---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 2749bc6c66d491a8a160d98b508fb43aa027b806
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398042"
---
# \<diagnostics>
<span data-ttu-id="db065-101">`diagnostics`Prvek definuje nastavení, které může být použito správcem pro kontrolu a kontrolu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="db065-101">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="db065-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db065-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics etwProviderId="String"
               performanceCounters="Off/ServiceOnly/All/Default"
               wmiProviderEnabled="Boolean">
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
    <messageLogging logEntireMessage="Boolean"
                    logMalformedMessages="Boolean"
                    logMessagesAtServiceLevel="Boolean"
                    logMessagesAtTransportLevel="Boolean"
                    maxMessagesToLog="Integer"
                    maxSizeOfMessageToLog="Integer">
      <filters>
        <clear />
      </filters>
    </messageLogging>
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db065-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="db065-103">Attributes and Elements</span></span>  
 <span data-ttu-id="db065-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="db065-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db065-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="db065-105">Attributes</span></span>  
  
|<span data-ttu-id="db065-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="db065-106">Attribute</span></span>|<span data-ttu-id="db065-107">Popis</span><span class="sxs-lookup"><span data-stu-id="db065-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="db065-108">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="db065-108">etwProviderId</span></span>|<span data-ttu-id="db065-109">Řetězec určující identifikátor poskytovatele trasování událostí, který zapisuje události do relací ETW.</span><span class="sxs-lookup"><span data-stu-id="db065-109">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="db065-110">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="db065-110">performanceCounters</span></span>|<span data-ttu-id="db065-111">Určuje, zda jsou povoleny čítače výkonu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="db065-111">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="db065-112">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="db065-112">Valid values are</span></span><br /><br /> <span data-ttu-id="db065-113">-Off: čítače výkonu jsou zakázané.</span><span class="sxs-lookup"><span data-stu-id="db065-113">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="db065-114">-ServiceOnly: jsou povoleny pouze čítače výkonu relevantní pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="db065-114">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="db065-115">-All: čítače výkonu lze zobrazit za běhu.</span><span class="sxs-lookup"><span data-stu-id="db065-115">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="db065-116">-Default: je vytvořená jediná instance čítače výkonu _WCF_Admin.</span><span class="sxs-lookup"><span data-stu-id="db065-116">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="db065-117">Tato instance slouží k povolení shromažďování dat technologie SQM pro použití v infrastruktuře.</span><span class="sxs-lookup"><span data-stu-id="db065-117">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="db065-118">Žádná z hodnot čítače této instance není aktualizována, a proto zůstane nula.</span><span class="sxs-lookup"><span data-stu-id="db065-118">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="db065-119">Toto je výchozí hodnota, pokud není pro WCF k dispozici žádná konfigurace.</span><span class="sxs-lookup"><span data-stu-id="db065-119">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="db065-120">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="db065-120">wmiProviderEnabled</span></span>|<span data-ttu-id="db065-121">Logická hodnota určující, zda je povolen zprostředkovatel rozhraní WMI pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="db065-121">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="db065-122">Zprostředkovatel rozhraní WMI je nutný pro uživatele, aby získal přístup k kontrolním a kontrolním funkcím Windows Communication Foundation (WCF) za běhu.</span><span class="sxs-lookup"><span data-stu-id="db065-122">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="db065-123">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="db065-123">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db065-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="db065-124">Child Elements</span></span>  
  
|<span data-ttu-id="db065-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="db065-125">Element</span></span>|<span data-ttu-id="db065-126">Description</span><span class="sxs-lookup"><span data-stu-id="db065-126">Description</span></span>|  
|-------------|-----------------|  
|[\<endToEndTracing>](endtoendtracing.md)|<span data-ttu-id="db065-127">Prvek konfigurace, který umožňuje povolit nebo zakázat různé aspekty komplexního trasování během běžící aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="db065-127">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[\<messageLogging>](messagelogging.md)|<span data-ttu-id="db065-128">Popisuje nastavení pro protokolování zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="db065-128">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="db065-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="db065-129">Parent Elements</span></span>  
  
|<span data-ttu-id="db065-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="db065-130">Element</span></span>|<span data-ttu-id="db065-131">Description</span><span class="sxs-lookup"><span data-stu-id="db065-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db065-132">serviceModel</span><span class="sxs-lookup"><span data-stu-id="db065-132">serviceModel</span></span>|<span data-ttu-id="db065-133">Kořenový element všech elementů konfigurace služby WCF.</span><span class="sxs-lookup"><span data-stu-id="db065-133">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db065-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db065-134">Remarks</span></span>  
 <span data-ttu-id="db065-135">`diagnostics`Oddíl definuje nastavení diagnostiky pro všechny služby, které jsou umístěny v sestavení.</span><span class="sxs-lookup"><span data-stu-id="db065-135">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="db065-136">Není možné definovat samostatné nastavení diagnostiky na úrovni služby, pokud v sestavení není pouze jedna služba.</span><span class="sxs-lookup"><span data-stu-id="db065-136">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="db065-137">Atributy jsou nastaveny podle požadavků oddílu.</span><span class="sxs-lookup"><span data-stu-id="db065-137">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db065-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="db065-138">Example</span></span>  
  
```xml  
<diagnostics wmiProviderEnabled="false"
             performanceCounters="all">
  <messageLogging logEntireMessage="true"
                  logMalformedMessages="true"
                  logMessagesAtServiceLevel="true"
                  logMessagesAtTransportLevel="true"
                  maxMessagesToLog="42"
                  maxSizeOfMessageToLog="42">
    <filters>
      <clear />
    </filters>
  </messageLogging>
</diagnostics>
```  
  
## <a name="see-also"></a><span data-ttu-id="db065-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="db065-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
