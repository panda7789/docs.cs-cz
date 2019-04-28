---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 3fc7828d399555f7c459f6dd067ce9a24b8998b6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704051"
---
# <a name="diagnostics"></a><span data-ttu-id="d6c11-101">\<Diagnostika ></span><span class="sxs-lookup"><span data-stu-id="d6c11-101">\<diagnostics></span></span>
<span data-ttu-id="d6c11-102">`diagnostics` Prvek definuje nastavení, které můžete použít správce pro řízení a kontrolu za běhu.</span><span class="sxs-lookup"><span data-stu-id="d6c11-102">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
 <span data-ttu-id="d6c11-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d6c11-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d6c11-104">\<Diagnostika ></span><span class="sxs-lookup"><span data-stu-id="d6c11-104">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6c11-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6c11-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6c11-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d6c11-106">Attributes and Elements</span></span>  
 <span data-ttu-id="d6c11-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d6c11-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6c11-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="d6c11-108">Attributes</span></span>  
  
|<span data-ttu-id="d6c11-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="d6c11-109">Attribute</span></span>|<span data-ttu-id="d6c11-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d6c11-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d6c11-111">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="d6c11-111">etwProviderId</span></span>|<span data-ttu-id="d6c11-112">Řetězec určující identifikátor poskytovatele trasování událostí, která zapisuje události do relací ETW.</span><span class="sxs-lookup"><span data-stu-id="d6c11-112">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="d6c11-113">performanceCounters</span><span class="sxs-lookup"><span data-stu-id="d6c11-113">performanceCounters</span></span>|<span data-ttu-id="d6c11-114">Určuje, zda jsou povoleny čítače výkonu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="d6c11-114">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="d6c11-115">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="d6c11-115">Valid values are</span></span><br /><br /> <span data-ttu-id="d6c11-116">-Vypnuto: Čítače výkonu jsou zakázány.</span><span class="sxs-lookup"><span data-stu-id="d6c11-116">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="d6c11-117">-ServiceOnly: Je povoleno pouze čítače výkonu relevantní pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="d6c11-117">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="d6c11-118">-Všechny: Čítače výkonu lze zobrazit v době běhu.</span><span class="sxs-lookup"><span data-stu-id="d6c11-118">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="d6c11-119">– Výchozí hodnota: Je vytvořen _WCF_Admin instance čítače výkonu jediné.</span><span class="sxs-lookup"><span data-stu-id="d6c11-119">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="d6c11-120">Tato instance se používá k povolení shromažďování dat technologie SQM pro používá infrastrukturu.</span><span class="sxs-lookup"><span data-stu-id="d6c11-120">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="d6c11-121">Žádné hodnoty čítače pro tuto instanci se aktualizují a proto bude i nadále na nule.</span><span class="sxs-lookup"><span data-stu-id="d6c11-121">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="d6c11-122">Toto je výchozí hodnota, pokud není k dispozici pro službu WCF žádná konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d6c11-122">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="d6c11-123">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="d6c11-123">wmiProviderEnabled</span></span>|<span data-ttu-id="d6c11-124">Logická hodnota, která určuje, zda je povolen zprostředkovatel rozhraní WMI pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="d6c11-124">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="d6c11-125">Zprostředkovatel rozhraní WMI pro uživatele je potřeba k získání přístupu za běhu k řízení a kontrolu funkce služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d6c11-125">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="d6c11-126">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="d6c11-126">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6c11-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d6c11-127">Child Elements</span></span>  
  
|<span data-ttu-id="d6c11-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="d6c11-128">Element</span></span>|<span data-ttu-id="d6c11-129">Popis</span><span class="sxs-lookup"><span data-stu-id="d6c11-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6c11-130">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="d6c11-130">\<endToEndTracing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endtoendtracing.md)|<span data-ttu-id="d6c11-131">Konfigurace element, který umožňuje povolit nebo zakázat různé aspekty začátku do konce trasování za běhu aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="d6c11-131">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[<span data-ttu-id="d6c11-132">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="d6c11-132">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)|<span data-ttu-id="d6c11-133">Popisuje nastavení pro protokolování zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="d6c11-133">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d6c11-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d6c11-134">Parent Elements</span></span>  
  
|<span data-ttu-id="d6c11-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="d6c11-135">Element</span></span>|<span data-ttu-id="d6c11-136">Popis</span><span class="sxs-lookup"><span data-stu-id="d6c11-136">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d6c11-137">serviceModel</span><span class="sxs-lookup"><span data-stu-id="d6c11-137">serviceModel</span></span>|<span data-ttu-id="d6c11-138">Kořenový element všechny elementy konfigurace WCF.</span><span class="sxs-lookup"><span data-stu-id="d6c11-138">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6c11-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6c11-139">Remarks</span></span>  
 <span data-ttu-id="d6c11-140">`diagnostics` Oddíl definuje nastavení diagnostiky pro všechny služby v sestavení.</span><span class="sxs-lookup"><span data-stu-id="d6c11-140">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="d6c11-141">Není možné definovat nastavení samostatné diagnostiky na úrovni služby, dokud není v sestavení pouze pro jednu službu.</span><span class="sxs-lookup"><span data-stu-id="d6c11-141">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="d6c11-142">Atributy se nastavují podle požadavků části.</span><span class="sxs-lookup"><span data-stu-id="d6c11-142">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6c11-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6c11-143">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d6c11-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6c11-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
