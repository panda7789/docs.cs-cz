---
title: <messageLogging>
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: 70fb2df1d37af23d9ec19932806989ce3329bf3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768911"
---
# <a name="messagelogging"></a><span data-ttu-id="a7208-101">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="a7208-101">\<messageLogging></span></span>
<span data-ttu-id="a7208-102">Tento prvek definuje nastavení možností protokolování zpráv Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a7208-102">This element defines the settings for the message-logging capabilities of Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="a7208-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a7208-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a7208-104">\<diagnostic></span><span class="sxs-lookup"><span data-stu-id="a7208-104">\<diagnostic></span></span>  
<span data-ttu-id="a7208-105">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="a7208-105">\<messageLogging></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7208-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7208-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7208-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a7208-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a7208-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a7208-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7208-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="a7208-109">Attributes</span></span>  
  
|<span data-ttu-id="a7208-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="a7208-110">Attribute</span></span>|<span data-ttu-id="a7208-111">Popis</span><span class="sxs-lookup"><span data-stu-id="a7208-111">Description</span></span>|  
|---------------|-----------------|  
|`logEntireMessage`|<span data-ttu-id="a7208-112">Logická hodnota určující, zda je zaznamenána celá zpráva (hlavička a tělo zprávy).</span><span class="sxs-lookup"><span data-stu-id="a7208-112">A Boolean value that specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="a7208-113">Výchozí hodnota je `false`, což znamená, že pouze záhlaví zprávy je zaznamenána.</span><span class="sxs-lookup"><span data-stu-id="a7208-113">The default is `false`, which means that only the message header is logged.</span></span> <span data-ttu-id="a7208-114">Toto nastavení ovlivňuje všechny úrovně protokolování zpráv (služba, přenos a chybně formátovaný).</span><span class="sxs-lookup"><span data-stu-id="a7208-114">This setting affects all message logging levels (service, transport, and malformed).</span></span>|  
|`logMalformedMessages`|<span data-ttu-id="a7208-115">Logická hodnota určující, zda jsou špatně vytvořené zprávy zaznamenány.</span><span class="sxs-lookup"><span data-stu-id="a7208-115">A Boolean value that specifies whether malformed messages are logged.</span></span> <span data-ttu-id="a7208-116">Špatně vytvořené zprávy se nepočítají do `maxMessagesToLog`.</span><span class="sxs-lookup"><span data-stu-id="a7208-116">Malformed messages do not count toward the `maxMessagesToLog`.</span></span> <span data-ttu-id="a7208-117">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="a7208-117">The default is `false`.</span></span>|  
|`logMessagesAtServiceLevel`|<span data-ttu-id="a7208-118">Logická hodnota určující, zda jsou zprávy trasovány na úrovni služby (před transformací související šifrování a transport).</span><span class="sxs-lookup"><span data-stu-id="a7208-118">A Boolean value that specifies whether messages are traced at the service level (before encryption- and transport-related transforms).</span></span> <span data-ttu-id="a7208-119">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="a7208-119">The default is `false`.</span></span>|  
|`logMessagesAtTransportLevel`|<span data-ttu-id="a7208-120">Logická hodnota určující, zda jsou zprávy trasovány na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="a7208-120">A Boolean value that specifies whether messages are traced at the transport level.</span></span> <span data-ttu-id="a7208-121">Jsou použity nějaké filtry zadané v konfiguračním souboru, a jsou trasovány pouze zprávy, které odpovídají filtrům.</span><span class="sxs-lookup"><span data-stu-id="a7208-121">Any filters specified in the config file are applied, and only messages that match the filters are traced.</span></span> <span data-ttu-id="a7208-122">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="a7208-122">The default is `false`.</span></span>|  
|`maxMessagesToLog`|<span data-ttu-id="a7208-123">Kladné celé číslo, které určuje maximální počet zaznamenavaných zpráv.</span><span class="sxs-lookup"><span data-stu-id="a7208-123">A positive integer that specifies the maximum number of messages to log.</span></span> <span data-ttu-id="a7208-124">Výchozí hodnota je 1000.</span><span class="sxs-lookup"><span data-stu-id="a7208-124">The default is 1000.</span></span>|  
|`maxSizeOfMessageToLog`|<span data-ttu-id="a7208-125">Kladné celé číslo, které určuje maximální velikost v bajtech zaznamenávané zprávy.</span><span class="sxs-lookup"><span data-stu-id="a7208-125">A positive integer that specifies the maximum size, in bytes, of a message to log.</span></span> <span data-ttu-id="a7208-126">Zprávy větší než limit se nebudou protokolovat.</span><span class="sxs-lookup"><span data-stu-id="a7208-126">Messages larger than the limit will not be logged.</span></span> <span data-ttu-id="a7208-127">Toto nastavení ovlivňuje všechny úrovně trasování.</span><span class="sxs-lookup"><span data-stu-id="a7208-127">This setting affects all trace levels.</span></span> <span data-ttu-id="a7208-128">Výchozí hodnota je 262144(0x4000).</span><span class="sxs-lookup"><span data-stu-id="a7208-128">The default is 262144(0x4000).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7208-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a7208-129">Child Elements</span></span>  
  
|<span data-ttu-id="a7208-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="a7208-130">Element</span></span>|<span data-ttu-id="a7208-131">Popis</span><span class="sxs-lookup"><span data-stu-id="a7208-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7208-132">filtry</span><span class="sxs-lookup"><span data-stu-id="a7208-132">filters</span></span>|<span data-ttu-id="a7208-133">`filters` Element obsahuje kolekci filtrů XPath.</span><span class="sxs-lookup"><span data-stu-id="a7208-133">The `filters` element holds a collection of XPath filters.</span></span> <span data-ttu-id="a7208-134">Pokud je povoleno protokolování zpráv přenosu (`logMessagesAtTransportLevel` je `true`), budou zaznamenány pouze zprávy odpovídající filtry.</span><span class="sxs-lookup"><span data-stu-id="a7208-134">When transport message logging is enabled (`logMessagesAtTransportLevel` is `true`), only messages matching the filters will be logged.</span></span><br /><br /> <span data-ttu-id="a7208-135">Filtry se použijí pouze na transportní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="a7208-135">Filters are applied only at the transport layer.</span></span> <span data-ttu-id="a7208-136">Protokolování úrovně a poškozené zprávy služby nejsou ovlivněny filtry.</span><span class="sxs-lookup"><span data-stu-id="a7208-136">Service level and malformed message logging are not affected by filters.</span></span><br /><br /> <span data-ttu-id="a7208-137">Atribut pouze pro tento element `filter`, je třída XpathFilter.</span><span class="sxs-lookup"><span data-stu-id="a7208-137">The only attribute for this element, `filter`, is an XpathFilter.</span></span><br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a><span data-ttu-id="a7208-138">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a7208-138">Parent Elements</span></span>  
  
|<span data-ttu-id="a7208-139">Prvek</span><span class="sxs-lookup"><span data-stu-id="a7208-139">Element</span></span>|<span data-ttu-id="a7208-140">Popis</span><span class="sxs-lookup"><span data-stu-id="a7208-140">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7208-141">diagnostika</span><span class="sxs-lookup"><span data-stu-id="a7208-141">diagnostics</span></span>|<span data-ttu-id="a7208-142">Definuje nastavení kontroly runtime WCF a ovládací prvek pro správce.</span><span class="sxs-lookup"><span data-stu-id="a7208-142">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7208-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a7208-143">Remarks</span></span>  
 <span data-ttu-id="a7208-144">Zprávy jsou zaznamenány na třech různých úrovních v zásobníku: služba, přenos a je poškozený.</span><span class="sxs-lookup"><span data-stu-id="a7208-144">Messages are logged at three different levels in the stack: service, transport, and malformed.</span></span> <span data-ttu-id="a7208-145">Každá úroveň lze aktivovat samostatně.</span><span class="sxs-lookup"><span data-stu-id="a7208-145">Each level can be activated separately.</span></span>  
  
 <span data-ttu-id="a7208-146">Filtry jazyka XPath lze přidat můžete protokolovat konkrétní zprávy na úrovni přenosu a služby.</span><span class="sxs-lookup"><span data-stu-id="a7208-146">XPath filters can be added to log specific messages at the transport and service levels.</span></span> <span data-ttu-id="a7208-147">Pokud jsou definovány žádné filtry, protokolují se všechny zprávy.</span><span class="sxs-lookup"><span data-stu-id="a7208-147">If no filters are defined, all messages are logged.</span></span> <span data-ttu-id="a7208-148">Filtry se použijí jenom u záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="a7208-148">Filters are applied only to the headers of the message.</span></span> <span data-ttu-id="a7208-149">Text se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="a7208-149">The body is ignored.</span></span> <span data-ttu-id="a7208-150">WCF ignoruje text zprávy pro zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="a7208-150">WCF ignores the message body to improve performance.</span></span> <span data-ttu-id="a7208-151">Pokud chcete filtrovat na základě obsahu těla, můžete vytvořit vlastní naslouchací proces s filtrem, která tak učiní.</span><span class="sxs-lookup"><span data-stu-id="a7208-151">If you want to filter based on the content of the body, you can create a custom listener with a filter that does so.</span></span>  
  
 <span data-ttu-id="a7208-152">Je potřeba vytvořit naslouchací proces trasování aktivujte trasování zprávy.</span><span class="sxs-lookup"><span data-stu-id="a7208-152">You need to create a trace listener to activate message tracing.</span></span> <span data-ttu-id="a7208-153">Naslouchací proces sám může být jakékoli naslouchací proces, který funguje s <xref:System.Diagnostics> architektura trasování.</span><span class="sxs-lookup"><span data-stu-id="a7208-153">The listener itself can be any listener that works with the <xref:System.Diagnostics> tracing architecture.</span></span> <span data-ttu-id="a7208-154">Následující příklad ukazuje, jak vytvořit takový naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="a7208-154">The following example demonstrates how to create such a listener.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="a7208-155">Příklad</span><span class="sxs-lookup"><span data-stu-id="a7208-155">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a7208-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7208-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [<span data-ttu-id="a7208-157">Konfigurace protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="a7208-157">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
