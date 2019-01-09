---
title: '&lt;messageLogging&gt;'
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: cfc5f23e58c5a428ecb4541ccfc0ada5b190fb36
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150445"
---
# <a name="ltmessagelogginggt"></a><span data-ttu-id="f4d35-102">&lt;messageLogging&gt;</span><span class="sxs-lookup"><span data-stu-id="f4d35-102">&lt;messageLogging&gt;</span></span>
<span data-ttu-id="f4d35-103">Tento prvek definuje nastavení možností protokolování zpráv Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f4d35-103">This element defines the settings for the message-logging capabilities of Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="f4d35-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f4d35-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f4d35-105">\<diagnostiky ></span><span class="sxs-lookup"><span data-stu-id="f4d35-105">\<diagnostic></span></span>  
<span data-ttu-id="f4d35-106">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="f4d35-106">\<messageLogging></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4d35-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4d35-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4d35-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f4d35-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f4d35-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f4d35-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4d35-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="f4d35-110">Attributes</span></span>  
  
|<span data-ttu-id="f4d35-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="f4d35-111">Attribute</span></span>|<span data-ttu-id="f4d35-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f4d35-112">Description</span></span>|  
|---------------|-----------------|  
|`logEntireMessage`|<span data-ttu-id="f4d35-113">Logická hodnota určující, zda je zaznamenána celá zpráva (hlavička a tělo zprávy).</span><span class="sxs-lookup"><span data-stu-id="f4d35-113">A Boolean value that specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="f4d35-114">Výchozí hodnota je `false`, což znamená, že pouze záhlaví zprávy je zaznamenána.</span><span class="sxs-lookup"><span data-stu-id="f4d35-114">The default is `false`, which means that only the message header is logged.</span></span> <span data-ttu-id="f4d35-115">Toto nastavení ovlivňuje všechny úrovně protokolování zpráv (služba, přenos a chybně formátovaný).</span><span class="sxs-lookup"><span data-stu-id="f4d35-115">This setting affects all message logging levels (service, transport, and malformed).</span></span>|  
|`logMalformedMessages`|<span data-ttu-id="f4d35-116">Logická hodnota určující, zda jsou špatně vytvořené zprávy zaznamenány.</span><span class="sxs-lookup"><span data-stu-id="f4d35-116">A Boolean value that specifies whether malformed messages are logged.</span></span> <span data-ttu-id="f4d35-117">Špatně vytvořené zprávy se nepočítají do `maxMessagesToLog`.</span><span class="sxs-lookup"><span data-stu-id="f4d35-117">Malformed messages do not count toward the `maxMessagesToLog`.</span></span> <span data-ttu-id="f4d35-118">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="f4d35-118">The default is `false`.</span></span>|  
|`logMessagesAtServiceLevel`|<span data-ttu-id="f4d35-119">Logická hodnota určující, zda jsou zprávy trasovány na úrovni služby (před transformací související šifrování a transport).</span><span class="sxs-lookup"><span data-stu-id="f4d35-119">A Boolean value that specifies whether messages are traced at the service level (before encryption- and transport-related transforms).</span></span> <span data-ttu-id="f4d35-120">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="f4d35-120">The default is `false`.</span></span>|  
|`logMessagesAtTransportLevel`|<span data-ttu-id="f4d35-121">Logická hodnota určující, zda jsou zprávy trasovány na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="f4d35-121">A Boolean value that specifies whether messages are traced at the transport level.</span></span> <span data-ttu-id="f4d35-122">Jsou použity nějaké filtry zadané v konfiguračním souboru, a jsou trasovány pouze zprávy, které odpovídají filtrům.</span><span class="sxs-lookup"><span data-stu-id="f4d35-122">Any filters specified in the config file are applied, and only messages that match the filters are traced.</span></span> <span data-ttu-id="f4d35-123">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="f4d35-123">The default is `false`.</span></span>|  
|`maxMessagesToLog`|<span data-ttu-id="f4d35-124">Kladné celé číslo, které určuje maximální počet zaznamenavaných zpráv.</span><span class="sxs-lookup"><span data-stu-id="f4d35-124">A positive integer that specifies the maximum number of messages to log.</span></span> <span data-ttu-id="f4d35-125">Výchozí hodnota je 1000.</span><span class="sxs-lookup"><span data-stu-id="f4d35-125">The default is 1000.</span></span>|  
|`maxSizeOfMessageToLog`|<span data-ttu-id="f4d35-126">Kladné celé číslo, které určuje maximální velikost v bajtech zaznamenávané zprávy.</span><span class="sxs-lookup"><span data-stu-id="f4d35-126">A positive integer that specifies the maximum size, in bytes, of a message to log.</span></span> <span data-ttu-id="f4d35-127">Zprávy větší než limit se nebudou protokolovat.</span><span class="sxs-lookup"><span data-stu-id="f4d35-127">Messages larger than the limit will not be logged.</span></span> <span data-ttu-id="f4d35-128">Toto nastavení ovlivňuje všechny úrovně trasování.</span><span class="sxs-lookup"><span data-stu-id="f4d35-128">This setting affects all trace levels.</span></span> <span data-ttu-id="f4d35-129">Výchozí hodnota je 262144(0x4000).</span><span class="sxs-lookup"><span data-stu-id="f4d35-129">The default is 262144(0x4000).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4d35-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f4d35-130">Child Elements</span></span>  
  
|<span data-ttu-id="f4d35-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="f4d35-131">Element</span></span>|<span data-ttu-id="f4d35-132">Popis</span><span class="sxs-lookup"><span data-stu-id="f4d35-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f4d35-133">filtry</span><span class="sxs-lookup"><span data-stu-id="f4d35-133">filters</span></span>|<span data-ttu-id="f4d35-134">`filters` Element obsahuje kolekci filtrů XPath.</span><span class="sxs-lookup"><span data-stu-id="f4d35-134">The `filters` element holds a collection of XPath filters.</span></span> <span data-ttu-id="f4d35-135">Pokud je povoleno protokolování zpráv přenosu (`logMessagesAtTransportLevel` je `true`), budou zaznamenány pouze zprávy odpovídající filtry.</span><span class="sxs-lookup"><span data-stu-id="f4d35-135">When transport message logging is enabled (`logMessagesAtTransportLevel` is `true`), only messages matching the filters will be logged.</span></span><br /><br /> <span data-ttu-id="f4d35-136">Filtry se použijí pouze na transportní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="f4d35-136">Filters are applied only at the transport layer.</span></span> <span data-ttu-id="f4d35-137">Protokolování úrovně a poškozené zprávy služby nejsou ovlivněny filtry.</span><span class="sxs-lookup"><span data-stu-id="f4d35-137">Service level and malformed message logging are not affected by filters.</span></span><br /><br /> <span data-ttu-id="f4d35-138">Atribut pouze pro tento element `filter`, je třída XpathFilter.</span><span class="sxs-lookup"><span data-stu-id="f4d35-138">The only attribute for this element, `filter`, is an XpathFilter.</span></span><br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a><span data-ttu-id="f4d35-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f4d35-139">Parent Elements</span></span>  
  
|<span data-ttu-id="f4d35-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="f4d35-140">Element</span></span>|<span data-ttu-id="f4d35-141">Popis</span><span class="sxs-lookup"><span data-stu-id="f4d35-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f4d35-142">diagnostika</span><span class="sxs-lookup"><span data-stu-id="f4d35-142">diagnostics</span></span>|<span data-ttu-id="f4d35-143">Definuje nastavení kontroly runtime WCF a ovládací prvek pro správce.</span><span class="sxs-lookup"><span data-stu-id="f4d35-143">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4d35-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f4d35-144">Remarks</span></span>  
 <span data-ttu-id="f4d35-145">Zprávy jsou zaznamenány na třech různých úrovních v zásobníku: služba, přenos a je poškozený.</span><span class="sxs-lookup"><span data-stu-id="f4d35-145">Messages are logged at three different levels in the stack: service, transport, and malformed.</span></span> <span data-ttu-id="f4d35-146">Každá úroveň lze aktivovat samostatně.</span><span class="sxs-lookup"><span data-stu-id="f4d35-146">Each level can be activated separately.</span></span>  
  
 <span data-ttu-id="f4d35-147">Filtry jazyka XPath lze přidat můžete protokolovat konkrétní zprávy na úrovni přenosu a služby.</span><span class="sxs-lookup"><span data-stu-id="f4d35-147">XPath filters can be added to log specific messages at the transport and service levels.</span></span> <span data-ttu-id="f4d35-148">Pokud jsou definovány žádné filtry, protokolují se všechny zprávy.</span><span class="sxs-lookup"><span data-stu-id="f4d35-148">If no filters are defined, all messages are logged.</span></span> <span data-ttu-id="f4d35-149">Filtry se použijí jenom u záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="f4d35-149">Filters are applied only to the headers of the message.</span></span> <span data-ttu-id="f4d35-150">Text se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="f4d35-150">The body is ignored.</span></span> <span data-ttu-id="f4d35-151">WCF ignoruje text zprávy pro zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="f4d35-151">WCF ignores the message body to improve performance.</span></span> <span data-ttu-id="f4d35-152">Pokud chcete filtrovat na základě obsahu těla, můžete vytvořit vlastní naslouchací proces s filtrem, která tak učiní.</span><span class="sxs-lookup"><span data-stu-id="f4d35-152">If you want to filter based on the content of the body, you can create a custom listener with a filter that does so.</span></span>  
  
 <span data-ttu-id="f4d35-153">Je potřeba vytvořit naslouchací proces trasování aktivujte trasování zprávy.</span><span class="sxs-lookup"><span data-stu-id="f4d35-153">You need to create a trace listener to activate message tracing.</span></span> <span data-ttu-id="f4d35-154">Naslouchací proces sám může být jakékoli naslouchací proces, který funguje s <xref:System.Diagnostics> architektura trasování.</span><span class="sxs-lookup"><span data-stu-id="f4d35-154">The listener itself can be any listener that works with the <xref:System.Diagnostics> tracing architecture.</span></span> <span data-ttu-id="f4d35-155">Následující příklad ukazuje, jak vytvořit takový naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="f4d35-155">The following example demonstrates how to create such a listener.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="f4d35-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="f4d35-156">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f4d35-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4d35-157">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>  
 [<span data-ttu-id="f4d35-158">Konfigurace protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="f4d35-158">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
