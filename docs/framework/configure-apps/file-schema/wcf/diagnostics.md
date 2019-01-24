---
title: '&lt;diagnostics&gt;'
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: de11145620e8fdf96785908df85ab5ecdfd2e25e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524587"
---
# <a name="ltdiagnosticsgt"></a><span data-ttu-id="f9c09-102">&lt;diagnostics&gt;</span><span class="sxs-lookup"><span data-stu-id="f9c09-102">&lt;diagnostics&gt;</span></span>
<span data-ttu-id="f9c09-103">`diagnostics` Prvek definuje nastavení, které můžete použít správce pro řízení a kontrolu za běhu.</span><span class="sxs-lookup"><span data-stu-id="f9c09-103">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
 <span data-ttu-id="f9c09-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f9c09-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f9c09-105">\<Diagnostika ></span><span class="sxs-lookup"><span data-stu-id="f9c09-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9c09-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9c09-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9c09-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f9c09-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f9c09-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f9c09-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9c09-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="f9c09-109">Attributes</span></span>  
  
|<span data-ttu-id="f9c09-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="f9c09-110">Attribute</span></span>|<span data-ttu-id="f9c09-111">Popis</span><span class="sxs-lookup"><span data-stu-id="f9c09-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f9c09-112">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="f9c09-112">etwProviderId</span></span>|<span data-ttu-id="f9c09-113">Řetězec určující identifikátor poskytovatele trasování událostí, která zapisuje události do relací ETW.</span><span class="sxs-lookup"><span data-stu-id="f9c09-113">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="f9c09-114">performanceCounters</span><span class="sxs-lookup"><span data-stu-id="f9c09-114">performanceCounters</span></span>|<span data-ttu-id="f9c09-115">Určuje, zda jsou povoleny čítače výkonu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="f9c09-115">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="f9c09-116">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="f9c09-116">Valid values are</span></span><br /><br /> <span data-ttu-id="f9c09-117">-Vypnuto: Čítače výkonu jsou zakázány.</span><span class="sxs-lookup"><span data-stu-id="f9c09-117">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="f9c09-118">-ServiceOnly: Je povoleno pouze čítače výkonu relevantní pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="f9c09-118">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="f9c09-119">-Všechny: Čítače výkonu lze zobrazit v době běhu.</span><span class="sxs-lookup"><span data-stu-id="f9c09-119">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="f9c09-120">– Výchozí hodnota: Je vytvořen _WCF_Admin instance čítače výkonu jediné.</span><span class="sxs-lookup"><span data-stu-id="f9c09-120">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="f9c09-121">Tato instance se používá k povolení shromažďování dat technologie SQM pro používá infrastrukturu.</span><span class="sxs-lookup"><span data-stu-id="f9c09-121">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="f9c09-122">Žádné hodnoty čítače pro tuto instanci se aktualizují a proto bude i nadále na nule.</span><span class="sxs-lookup"><span data-stu-id="f9c09-122">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="f9c09-123">Toto je výchozí hodnota, pokud není k dispozici pro službu WCF žádná konfigurace.</span><span class="sxs-lookup"><span data-stu-id="f9c09-123">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="f9c09-124">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="f9c09-124">wmiProviderEnabled</span></span>|<span data-ttu-id="f9c09-125">Logická hodnota, která určuje, zda je povolen zprostředkovatel rozhraní WMI pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="f9c09-125">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="f9c09-126">Zprostředkovatel rozhraní WMI pro uživatele je potřeba k získání přístupu za běhu k řízení a kontrolu funkce služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f9c09-126">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="f9c09-127">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="f9c09-127">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9c09-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f9c09-128">Child Elements</span></span>  
  
|<span data-ttu-id="f9c09-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="f9c09-129">Element</span></span>|<span data-ttu-id="f9c09-130">Popis</span><span class="sxs-lookup"><span data-stu-id="f9c09-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9c09-131">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="f9c09-131">\<endToEndTracing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endtoendtracing.md)|<span data-ttu-id="f9c09-132">Konfigurace element, který umožňuje povolit nebo zakázat různé aspekty začátku do konce trasování za běhu aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="f9c09-132">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[<span data-ttu-id="f9c09-133">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="f9c09-133">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)|<span data-ttu-id="f9c09-134">Popisuje nastavení pro protokolování zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="f9c09-134">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f9c09-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f9c09-135">Parent Elements</span></span>  
  
|<span data-ttu-id="f9c09-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="f9c09-136">Element</span></span>|<span data-ttu-id="f9c09-137">Popis</span><span class="sxs-lookup"><span data-stu-id="f9c09-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f9c09-138">serviceModel</span><span class="sxs-lookup"><span data-stu-id="f9c09-138">serviceModel</span></span>|<span data-ttu-id="f9c09-139">Kořenový element všechny elementy konfigurace WCF.</span><span class="sxs-lookup"><span data-stu-id="f9c09-139">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9c09-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f9c09-140">Remarks</span></span>  
 <span data-ttu-id="f9c09-141">`diagnostics` Oddíl definuje nastavení diagnostiky pro všechny služby v sestavení.</span><span class="sxs-lookup"><span data-stu-id="f9c09-141">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="f9c09-142">Není možné definovat nastavení samostatné diagnostiky na úrovni služby, dokud není v sestavení pouze pro jednu službu.</span><span class="sxs-lookup"><span data-stu-id="f9c09-142">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="f9c09-143">Atributy se nastavují podle požadavků části.</span><span class="sxs-lookup"><span data-stu-id="f9c09-143">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9c09-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9c09-144">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f9c09-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9c09-145">See also</span></span>
- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
