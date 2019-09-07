---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 2749bc6c66d491a8a160d98b508fb43aa027b806
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398042"
---
# <a name="diagnostics"></a><span data-ttu-id="8415d-101">\<> diagnostiky</span><span class="sxs-lookup"><span data-stu-id="8415d-101">\<diagnostics></span></span>
<span data-ttu-id="8415d-102">`diagnostics` Prvek definuje nastavení, které může být použito správcem pro kontrolu a kontrolu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="8415d-102">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
<span data-ttu-id="8415d-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8415d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8415d-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8415d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8415d-105">&nbsp;&nbsp;&nbsp;&nbsp; **\<> diagnostiky**</span><span class="sxs-lookup"><span data-stu-id="8415d-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8415d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8415d-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8415d-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8415d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="8415d-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8415d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8415d-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="8415d-109">Attributes</span></span>  
  
|<span data-ttu-id="8415d-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="8415d-110">Attribute</span></span>|<span data-ttu-id="8415d-111">Popis</span><span class="sxs-lookup"><span data-stu-id="8415d-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8415d-112">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="8415d-112">etwProviderId</span></span>|<span data-ttu-id="8415d-113">Řetězec určující identifikátor poskytovatele trasování událostí, který zapisuje události do relací ETW.</span><span class="sxs-lookup"><span data-stu-id="8415d-113">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="8415d-114">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="8415d-114">performanceCounters</span></span>|<span data-ttu-id="8415d-115">Určuje, zda jsou povoleny čítače výkonu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="8415d-115">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="8415d-116">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="8415d-116">Valid values are</span></span><br /><br /> <span data-ttu-id="8415d-117">Zaokrouhl Čítače výkonu jsou zakázané.</span><span class="sxs-lookup"><span data-stu-id="8415d-117">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="8415d-118">- ServiceOnly: Jsou povoleny pouze čítače výkonu relevantní pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="8415d-118">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="8415d-119">Všem Čítače výkonu lze zobrazit za běhu.</span><span class="sxs-lookup"><span data-stu-id="8415d-119">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="8415d-120">Výchozí Vytvoří se jedna instance čítače výkonu _WCF_Admin.</span><span class="sxs-lookup"><span data-stu-id="8415d-120">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="8415d-121">Tato instance slouží k povolení shromažďování dat technologie SQM pro použití v infrastruktuře.</span><span class="sxs-lookup"><span data-stu-id="8415d-121">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="8415d-122">Žádná z hodnot čítače této instance není aktualizována, a proto zůstane nula.</span><span class="sxs-lookup"><span data-stu-id="8415d-122">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="8415d-123">Toto je výchozí hodnota, pokud není pro WCF k dispozici žádná konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8415d-123">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="8415d-124">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="8415d-124">wmiProviderEnabled</span></span>|<span data-ttu-id="8415d-125">Logická hodnota určující, zda je povolen zprostředkovatel rozhraní WMI pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="8415d-125">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="8415d-126">Zprostředkovatel rozhraní WMI je nutný pro uživatele, aby získal přístup k kontrolním a kontrolním funkcím Windows Communication Foundation (WCF) za běhu.</span><span class="sxs-lookup"><span data-stu-id="8415d-126">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="8415d-127">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="8415d-127">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8415d-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8415d-128">Child Elements</span></span>  
  
|<span data-ttu-id="8415d-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="8415d-129">Element</span></span>|<span data-ttu-id="8415d-130">Popis</span><span class="sxs-lookup"><span data-stu-id="8415d-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8415d-131">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="8415d-131">\<endToEndTracing></span></span>](endtoendtracing.md)|<span data-ttu-id="8415d-132">Prvek konfigurace, který umožňuje povolit nebo zakázat různé aspekty komplexního trasování během běžící aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="8415d-132">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[<span data-ttu-id="8415d-133">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="8415d-133">\<messageLogging></span></span>](messagelogging.md)|<span data-ttu-id="8415d-134">Popisuje nastavení pro protokolování zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="8415d-134">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8415d-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8415d-135">Parent Elements</span></span>  
  
|<span data-ttu-id="8415d-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="8415d-136">Element</span></span>|<span data-ttu-id="8415d-137">Popis</span><span class="sxs-lookup"><span data-stu-id="8415d-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8415d-138">serviceModel</span><span class="sxs-lookup"><span data-stu-id="8415d-138">serviceModel</span></span>|<span data-ttu-id="8415d-139">Kořenový element všech elementů konfigurace služby WCF.</span><span class="sxs-lookup"><span data-stu-id="8415d-139">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8415d-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8415d-140">Remarks</span></span>  
 <span data-ttu-id="8415d-141">`diagnostics` Oddíl definuje nastavení diagnostiky pro všechny služby, které jsou umístěny v sestavení.</span><span class="sxs-lookup"><span data-stu-id="8415d-141">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="8415d-142">Není možné definovat samostatné nastavení diagnostiky na úrovni služby, pokud v sestavení není pouze jedna služba.</span><span class="sxs-lookup"><span data-stu-id="8415d-142">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="8415d-143">Atributy jsou nastaveny podle požadavků oddílu.</span><span class="sxs-lookup"><span data-stu-id="8415d-143">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8415d-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="8415d-144">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8415d-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8415d-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
