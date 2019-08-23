---
title: <messageLogging>
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: f54028489ec5aa34ae38115d7a582b01b9da92f9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931415"
---
# <a name="messagelogging"></a><span data-ttu-id="e3bb1-101">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="e3bb1-101">\<messageLogging></span></span>
<span data-ttu-id="e3bb1-102">Tento prvek definuje nastavení možností protokolování zpráv Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e3bb1-102">This element defines the settings for the message-logging capabilities of Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="e3bb1-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e3bb1-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e3bb1-104">\<> diagnostiky</span><span class="sxs-lookup"><span data-stu-id="e3bb1-104">\<diagnostic></span></span>  
<span data-ttu-id="e3bb1-105">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="e3bb1-105">\<messageLogging></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3bb1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3bb1-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3bb1-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e3bb1-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e3bb1-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3bb1-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="e3bb1-109">Attributes</span></span>  
  
|<span data-ttu-id="e3bb1-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="e3bb1-110">Attribute</span></span>|<span data-ttu-id="e3bb1-111">Popis</span><span class="sxs-lookup"><span data-stu-id="e3bb1-111">Description</span></span>|  
|---------------|-----------------|  
|`logEntireMessage`|<span data-ttu-id="e3bb1-112">Logická hodnota, která určuje, zda má být zaznamenána celá zpráva (hlavička a tělo zprávy).</span><span class="sxs-lookup"><span data-stu-id="e3bb1-112">A Boolean value that specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="e3bb1-113">Výchozí hodnota je `false`, což znamená, že je protokolována pouze Hlavička zprávy.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-113">The default is `false`, which means that only the message header is logged.</span></span> <span data-ttu-id="e3bb1-114">Toto nastavení má vliv na všechny úrovně protokolování zpráv (služba, přenos a nesprávně vytvořená).</span><span class="sxs-lookup"><span data-stu-id="e3bb1-114">This setting affects all message logging levels (service, transport, and malformed).</span></span>|  
|`logMalformedMessages`|<span data-ttu-id="e3bb1-115">Logická hodnota, která určuje, zda jsou špatně vytvořené zprávy zaznamenány.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-115">A Boolean value that specifies whether malformed messages are logged.</span></span> <span data-ttu-id="e3bb1-116">Poškozené zprávy se nepočítají směrem k `maxMessagesToLog`.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-116">Malformed messages do not count toward the `maxMessagesToLog`.</span></span> <span data-ttu-id="e3bb1-117">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-117">The default is `false`.</span></span>|  
|`logMessagesAtServiceLevel`|<span data-ttu-id="e3bb1-118">Logická hodnota, která určuje, zda jsou zprávy trasovány na úrovni služby (před transformací související s šifrováním a přenosem).</span><span class="sxs-lookup"><span data-stu-id="e3bb1-118">A Boolean value that specifies whether messages are traced at the service level (before encryption- and transport-related transforms).</span></span> <span data-ttu-id="e3bb1-119">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-119">The default is `false`.</span></span>|  
|`logMessagesAtTransportLevel`|<span data-ttu-id="e3bb1-120">Logická hodnota, která určuje, zda jsou zprávy trasovány na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-120">A Boolean value that specifies whether messages are traced at the transport level.</span></span> <span data-ttu-id="e3bb1-121">Všechny filtry zadané v konfiguračním souboru jsou aplikovány a budou trasovány pouze zprávy, které odpovídají filtrům.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-121">Any filters specified in the config file are applied, and only messages that match the filters are traced.</span></span> <span data-ttu-id="e3bb1-122">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-122">The default is `false`.</span></span>|  
|`maxMessagesToLog`|<span data-ttu-id="e3bb1-123">Celé kladné číslo určující maximální počet zpráv, které mají být protokolovány.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-123">A positive integer that specifies the maximum number of messages to log.</span></span> <span data-ttu-id="e3bb1-124">Výchozí hodnota je 1000.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-124">The default is 1000.</span></span>|  
|`maxSizeOfMessageToLog`|<span data-ttu-id="e3bb1-125">Celé kladné číslo určující maximální velikost zprávy, která se má protokolovat (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="e3bb1-125">A positive integer that specifies the maximum size, in bytes, of a message to log.</span></span> <span data-ttu-id="e3bb1-126">Zprávy větší, než je limit, nebudou protokolovány.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-126">Messages larger than the limit will not be logged.</span></span> <span data-ttu-id="e3bb1-127">Toto nastavení má vliv na všechny úrovně trasování.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-127">This setting affects all trace levels.</span></span> <span data-ttu-id="e3bb1-128">Výchozí hodnota je 262144 (0x4000).</span><span class="sxs-lookup"><span data-stu-id="e3bb1-128">The default is 262144(0x4000).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3bb1-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e3bb1-129">Child Elements</span></span>  
  
|<span data-ttu-id="e3bb1-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="e3bb1-130">Element</span></span>|<span data-ttu-id="e3bb1-131">Popis</span><span class="sxs-lookup"><span data-stu-id="e3bb1-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e3bb1-132">filtry</span><span class="sxs-lookup"><span data-stu-id="e3bb1-132">filters</span></span>|<span data-ttu-id="e3bb1-133">`filters` Element obsahuje kolekci filtrů XPath.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-133">The `filters` element holds a collection of XPath filters.</span></span> <span data-ttu-id="e3bb1-134">Pokud je povoleno protokolování přenosové zprávy`logMessagesAtTransportLevel` ( `true`je), budou protokolovány pouze zprávy, které odpovídají filtrům.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-134">When transport message logging is enabled (`logMessagesAtTransportLevel` is `true`), only messages matching the filters will be logged.</span></span><br /><br /> <span data-ttu-id="e3bb1-135">Filtry se aplikují jenom na transportní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-135">Filters are applied only at the transport layer.</span></span> <span data-ttu-id="e3bb1-136">Filtry neovlivní úroveň služeb a nesprávně přihlašování zpráv.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-136">Service level and malformed message logging are not affected by filters.</span></span><br /><br /> <span data-ttu-id="e3bb1-137">Jediný atribut pro tento prvek `filter`, je Třída XPathFilter.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-137">The only attribute for this element, `filter`, is an XpathFilter.</span></span><br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a><span data-ttu-id="e3bb1-138">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e3bb1-138">Parent Elements</span></span>  
  
|<span data-ttu-id="e3bb1-139">Prvek</span><span class="sxs-lookup"><span data-stu-id="e3bb1-139">Element</span></span>|<span data-ttu-id="e3bb1-140">Popis</span><span class="sxs-lookup"><span data-stu-id="e3bb1-140">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e3bb1-141">diagnostika</span><span class="sxs-lookup"><span data-stu-id="e3bb1-141">diagnostics</span></span>|<span data-ttu-id="e3bb1-142">Definuje nastavení WCF pro kontrolu a kontrolu za běhu pro správce.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-142">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3bb1-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e3bb1-143">Remarks</span></span>  
 <span data-ttu-id="e3bb1-144">Zprávy jsou protokolovány na třech různých úrovních zásobníku: služba, Transport a poškozená.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-144">Messages are logged at three different levels in the stack: service, transport, and malformed.</span></span> <span data-ttu-id="e3bb1-145">Jednotlivé úrovně lze aktivovat samostatně.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-145">Each level can be activated separately.</span></span>  
  
 <span data-ttu-id="e3bb1-146">Filtry XPath lze přidat do protokolu pro zprávy specifické pro přenos a úrovně služeb.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-146">XPath filters can be added to log specific messages at the transport and service levels.</span></span> <span data-ttu-id="e3bb1-147">Pokud nejsou definovány žádné filtry, budou protokolovány všechny zprávy.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-147">If no filters are defined, all messages are logged.</span></span> <span data-ttu-id="e3bb1-148">Filtry se aplikují pouze na záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-148">Filters are applied only to the headers of the message.</span></span> <span data-ttu-id="e3bb1-149">Tělo je ignorováno.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-149">The body is ignored.</span></span> <span data-ttu-id="e3bb1-150">WCF ignoruje tělo zprávy za účelem zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-150">WCF ignores the message body to improve performance.</span></span> <span data-ttu-id="e3bb1-151">Pokud chcete filtrovat podle obsahu těla, můžete vytvořit vlastní naslouchací proces s filtrem, který to dělá.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-151">If you want to filter based on the content of the body, you can create a custom listener with a filter that does so.</span></span>  
  
 <span data-ttu-id="e3bb1-152">Chcete-li aktivovat trasování zpráv, je nutné vytvořit naslouchací proces trasování.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-152">You need to create a trace listener to activate message tracing.</span></span> <span data-ttu-id="e3bb1-153">Naslouchací proces může být libovolný naslouchací proces, který pracuje s <xref:System.Diagnostics> architekturou trasování.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-153">The listener itself can be any listener that works with the <xref:System.Diagnostics> tracing architecture.</span></span> <span data-ttu-id="e3bb1-154">Následující příklad ukazuje, jak vytvořit takový naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="e3bb1-154">The following example demonstrates how to create such a listener.</span></span>  
  
```xml  
<system.diagnostics>
  <sources>
    <source name="System.ServiceModel"
            switchValue="Verbose">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="ServiceModel Listener"
             traceOutputOptions="None" />
      </listeners>
    </source>
    <source name="System.ServiceModel.MessageLogging">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="MessageLogging Listener"
             traceOutputOptions="None" />
      </listeners>
    </source>
  </sources>
  <sharedListeners>
    <add initializeData="C:\ItProTools\TraceLog.xml"
         type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         name="ServiceModel Listener"
         traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />
    <add initializeData="C:\ItProTools\MessageLog.log"
         type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         name="MessageLogging Listener"
         traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />
  </sharedListeners>
</system.diagnostics>
```  
  
## <a name="example"></a><span data-ttu-id="e3bb1-155">Příklad</span><span class="sxs-lookup"><span data-stu-id="e3bb1-155">Example</span></span>  
  
```xml  
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
```  
  
## <a name="see-also"></a><span data-ttu-id="e3bb1-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3bb1-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [<span data-ttu-id="e3bb1-157">Konfigurace protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="e3bb1-157">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
