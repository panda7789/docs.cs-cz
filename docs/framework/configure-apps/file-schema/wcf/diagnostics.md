---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 170cae5b328c86073c1d8e7710bb19e98ab5688c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925879"
---
# <a name="diagnostics"></a><span data-ttu-id="a42d7-101">\<> diagnostiky</span><span class="sxs-lookup"><span data-stu-id="a42d7-101">\<diagnostics></span></span>
<span data-ttu-id="a42d7-102">`diagnostics` Prvek definuje nastavení, které může být použito správcem pro kontrolu a kontrolu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="a42d7-102">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
 <span data-ttu-id="a42d7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a42d7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a42d7-104">\<> diagnostiky</span><span class="sxs-lookup"><span data-stu-id="a42d7-104">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a42d7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a42d7-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a42d7-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a42d7-106">Attributes and Elements</span></span>  
 <span data-ttu-id="a42d7-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a42d7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a42d7-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="a42d7-108">Attributes</span></span>  
  
|<span data-ttu-id="a42d7-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="a42d7-109">Attribute</span></span>|<span data-ttu-id="a42d7-110">Popis</span><span class="sxs-lookup"><span data-stu-id="a42d7-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a42d7-111">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="a42d7-111">etwProviderId</span></span>|<span data-ttu-id="a42d7-112">Řetězec určující identifikátor poskytovatele trasování událostí, který zapisuje události do relací ETW.</span><span class="sxs-lookup"><span data-stu-id="a42d7-112">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="a42d7-113">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="a42d7-113">performanceCounters</span></span>|<span data-ttu-id="a42d7-114">Určuje, zda jsou povoleny čítače výkonu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="a42d7-114">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="a42d7-115">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="a42d7-115">Valid values are</span></span><br /><br /> <span data-ttu-id="a42d7-116">Zaokrouhl Čítače výkonu jsou zakázané.</span><span class="sxs-lookup"><span data-stu-id="a42d7-116">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="a42d7-117">- ServiceOnly: Jsou povoleny pouze čítače výkonu relevantní pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="a42d7-117">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="a42d7-118">Všem Čítače výkonu lze zobrazit za běhu.</span><span class="sxs-lookup"><span data-stu-id="a42d7-118">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="a42d7-119">Výchozí Vytvoří se jedna instance čítače výkonu _WCF_Admin.</span><span class="sxs-lookup"><span data-stu-id="a42d7-119">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="a42d7-120">Tato instance slouží k povolení shromažďování dat technologie SQM pro použití v infrastruktuře.</span><span class="sxs-lookup"><span data-stu-id="a42d7-120">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="a42d7-121">Žádná z hodnot čítače této instance není aktualizována, a proto zůstane nula.</span><span class="sxs-lookup"><span data-stu-id="a42d7-121">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="a42d7-122">Toto je výchozí hodnota, pokud není pro WCF k dispozici žádná konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a42d7-122">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="a42d7-123">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="a42d7-123">wmiProviderEnabled</span></span>|<span data-ttu-id="a42d7-124">Logická hodnota určující, zda je povolen zprostředkovatel rozhraní WMI pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="a42d7-124">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="a42d7-125">Zprostředkovatel rozhraní WMI je nutný pro uživatele, aby získal přístup k kontrolním a kontrolním funkcím Windows Communication Foundation (WCF) za běhu.</span><span class="sxs-lookup"><span data-stu-id="a42d7-125">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="a42d7-126">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="a42d7-126">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a42d7-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a42d7-127">Child Elements</span></span>  
  
|<span data-ttu-id="a42d7-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="a42d7-128">Element</span></span>|<span data-ttu-id="a42d7-129">Popis</span><span class="sxs-lookup"><span data-stu-id="a42d7-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a42d7-130">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="a42d7-130">\<endToEndTracing></span></span>](endtoendtracing.md)|<span data-ttu-id="a42d7-131">Prvek konfigurace, který umožňuje povolit nebo zakázat různé aspekty komplexního trasování během běžící aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="a42d7-131">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[<span data-ttu-id="a42d7-132">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="a42d7-132">\<messageLogging></span></span>](messagelogging.md)|<span data-ttu-id="a42d7-133">Popisuje nastavení pro protokolování zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="a42d7-133">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a42d7-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a42d7-134">Parent Elements</span></span>  
  
|<span data-ttu-id="a42d7-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="a42d7-135">Element</span></span>|<span data-ttu-id="a42d7-136">Popis</span><span class="sxs-lookup"><span data-stu-id="a42d7-136">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a42d7-137">serviceModel</span><span class="sxs-lookup"><span data-stu-id="a42d7-137">serviceModel</span></span>|<span data-ttu-id="a42d7-138">Kořenový element všech elementů konfigurace služby WCF.</span><span class="sxs-lookup"><span data-stu-id="a42d7-138">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a42d7-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a42d7-139">Remarks</span></span>  
 <span data-ttu-id="a42d7-140">`diagnostics` Oddíl definuje nastavení diagnostiky pro všechny služby, které jsou umístěny v sestavení.</span><span class="sxs-lookup"><span data-stu-id="a42d7-140">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="a42d7-141">Není možné definovat samostatné nastavení diagnostiky na úrovni služby, pokud v sestavení není pouze jedna služba.</span><span class="sxs-lookup"><span data-stu-id="a42d7-141">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="a42d7-142">Atributy jsou nastaveny podle požadavků oddílu.</span><span class="sxs-lookup"><span data-stu-id="a42d7-142">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a42d7-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="a42d7-143">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a42d7-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a42d7-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
