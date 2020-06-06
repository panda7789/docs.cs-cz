---
title: <messageLogging>
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: 9291c38af28c18d20e23e34e8316b4a9fe523123
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855118"
---
# \<messageLogging>
<span data-ttu-id="96239-101">Tento prvek definuje nastavení možností protokolování zpráv Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="96239-101">This element defines the settings for the message-logging capabilities of Windows Communication Foundation (WCF).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageLogging>**  
  
## <a name="syntax"></a><span data-ttu-id="96239-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96239-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96239-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="96239-103">Attributes and Elements</span></span>  
 <span data-ttu-id="96239-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="96239-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96239-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="96239-105">Attributes</span></span>  
  
|<span data-ttu-id="96239-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="96239-106">Attribute</span></span>|<span data-ttu-id="96239-107">Popis</span><span class="sxs-lookup"><span data-stu-id="96239-107">Description</span></span>|  
|---------------|-----------------|  
|`logEntireMessage`|<span data-ttu-id="96239-108">Logická hodnota, která určuje, zda má být zaznamenána celá zpráva (hlavička a tělo zprávy).</span><span class="sxs-lookup"><span data-stu-id="96239-108">A Boolean value that specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="96239-109">Výchozí hodnota je `false` , což znamená, že je protokolována pouze Hlavička zprávy.</span><span class="sxs-lookup"><span data-stu-id="96239-109">The default is `false`, which means that only the message header is logged.</span></span> <span data-ttu-id="96239-110">Toto nastavení má vliv na všechny úrovně protokolování zpráv (služba, přenos a nesprávně vytvořená).</span><span class="sxs-lookup"><span data-stu-id="96239-110">This setting affects all message logging levels (service, transport, and malformed).</span></span>|  
|`logMalformedMessages`|<span data-ttu-id="96239-111">Logická hodnota, která určuje, zda jsou špatně vytvořené zprávy zaznamenány.</span><span class="sxs-lookup"><span data-stu-id="96239-111">A Boolean value that specifies whether malformed messages are logged.</span></span> <span data-ttu-id="96239-112">Poškozené zprávy se nepočítají směrem k `maxMessagesToLog` .</span><span class="sxs-lookup"><span data-stu-id="96239-112">Malformed messages do not count toward the `maxMessagesToLog`.</span></span> <span data-ttu-id="96239-113">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="96239-113">The default is `false`.</span></span>|  
|`logMessagesAtServiceLevel`|<span data-ttu-id="96239-114">Logická hodnota, která určuje, zda jsou zprávy trasovány na úrovni služby (před transformací související s šifrováním a přenosem).</span><span class="sxs-lookup"><span data-stu-id="96239-114">A Boolean value that specifies whether messages are traced at the service level (before encryption- and transport-related transforms).</span></span> <span data-ttu-id="96239-115">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="96239-115">The default is `false`.</span></span>|  
|`logMessagesAtTransportLevel`|<span data-ttu-id="96239-116">Logická hodnota, která určuje, zda jsou zprávy trasovány na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="96239-116">A Boolean value that specifies whether messages are traced at the transport level.</span></span> <span data-ttu-id="96239-117">Všechny filtry zadané v konfiguračním souboru jsou aplikovány a budou trasovány pouze zprávy, které odpovídají filtrům.</span><span class="sxs-lookup"><span data-stu-id="96239-117">Any filters specified in the config file are applied, and only messages that match the filters are traced.</span></span> <span data-ttu-id="96239-118">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="96239-118">The default is `false`.</span></span>|  
|`maxMessagesToLog`|<span data-ttu-id="96239-119">Celé kladné číslo určující maximální počet zpráv, které mají být protokolovány.</span><span class="sxs-lookup"><span data-stu-id="96239-119">A positive integer that specifies the maximum number of messages to log.</span></span> <span data-ttu-id="96239-120">Výchozí hodnota je 1 000.</span><span class="sxs-lookup"><span data-stu-id="96239-120">The default is 1000.</span></span>|  
|`maxSizeOfMessageToLog`|<span data-ttu-id="96239-121">Celé kladné číslo určující maximální velikost zprávy, která se má protokolovat (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="96239-121">A positive integer that specifies the maximum size, in bytes, of a message to log.</span></span> <span data-ttu-id="96239-122">Zprávy větší, než je limit, nebudou protokolovány.</span><span class="sxs-lookup"><span data-stu-id="96239-122">Messages larger than the limit will not be logged.</span></span> <span data-ttu-id="96239-123">Toto nastavení má vliv na všechny úrovně trasování.</span><span class="sxs-lookup"><span data-stu-id="96239-123">This setting affects all trace levels.</span></span> <span data-ttu-id="96239-124">Výchozí hodnota je 262144 (0x4000).</span><span class="sxs-lookup"><span data-stu-id="96239-124">The default is 262144(0x4000).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="96239-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="96239-125">Child Elements</span></span>  
  
|<span data-ttu-id="96239-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="96239-126">Element</span></span>|<span data-ttu-id="96239-127">Description</span><span class="sxs-lookup"><span data-stu-id="96239-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="96239-128">filtry</span><span class="sxs-lookup"><span data-stu-id="96239-128">filters</span></span>|<span data-ttu-id="96239-129">`filters`Element obsahuje kolekci filtrů XPath.</span><span class="sxs-lookup"><span data-stu-id="96239-129">The `filters` element holds a collection of XPath filters.</span></span> <span data-ttu-id="96239-130">Pokud je povoleno protokolování přenosové zprávy ( `logMessagesAtTransportLevel` je `true` ), budou protokolovány pouze zprávy, které odpovídají filtrům.</span><span class="sxs-lookup"><span data-stu-id="96239-130">When transport message logging is enabled (`logMessagesAtTransportLevel` is `true`), only messages matching the filters will be logged.</span></span><br /><br /> <span data-ttu-id="96239-131">Filtry se aplikují jenom na transportní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="96239-131">Filters are applied only at the transport layer.</span></span> <span data-ttu-id="96239-132">Filtry neovlivní úroveň služeb a nesprávně přihlašování zpráv.</span><span class="sxs-lookup"><span data-stu-id="96239-132">Service level and malformed message logging are not affected by filters.</span></span><br /><br /> <span data-ttu-id="96239-133">Jediný atribut pro tento prvek, `filter` je Třída XPathFilter.</span><span class="sxs-lookup"><span data-stu-id="96239-133">The only attribute for this element, `filter`, is an XpathFilter.</span></span><br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a><span data-ttu-id="96239-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="96239-134">Parent Elements</span></span>  
  
|<span data-ttu-id="96239-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="96239-135">Element</span></span>|<span data-ttu-id="96239-136">Description</span><span class="sxs-lookup"><span data-stu-id="96239-136">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="96239-137">Diagnostika</span><span class="sxs-lookup"><span data-stu-id="96239-137">diagnostics</span></span>|<span data-ttu-id="96239-138">Definuje nastavení WCF pro kontrolu a kontrolu za běhu pro správce.</span><span class="sxs-lookup"><span data-stu-id="96239-138">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96239-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96239-139">Remarks</span></span>  
 <span data-ttu-id="96239-140">Zprávy jsou protokolovány na třech různých úrovních zásobníku: služba, Transport a poškozená.</span><span class="sxs-lookup"><span data-stu-id="96239-140">Messages are logged at three different levels in the stack: service, transport, and malformed.</span></span> <span data-ttu-id="96239-141">Jednotlivé úrovně lze aktivovat samostatně.</span><span class="sxs-lookup"><span data-stu-id="96239-141">Each level can be activated separately.</span></span>  
  
 <span data-ttu-id="96239-142">Filtry XPath lze přidat do protokolu pro zprávy specifické pro přenos a úrovně služeb.</span><span class="sxs-lookup"><span data-stu-id="96239-142">XPath filters can be added to log specific messages at the transport and service levels.</span></span> <span data-ttu-id="96239-143">Pokud nejsou definovány žádné filtry, budou protokolovány všechny zprávy.</span><span class="sxs-lookup"><span data-stu-id="96239-143">If no filters are defined, all messages are logged.</span></span> <span data-ttu-id="96239-144">Filtry se aplikují pouze na záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="96239-144">Filters are applied only to the headers of the message.</span></span> <span data-ttu-id="96239-145">Tělo je ignorováno.</span><span class="sxs-lookup"><span data-stu-id="96239-145">The body is ignored.</span></span> <span data-ttu-id="96239-146">WCF ignoruje tělo zprávy za účelem zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="96239-146">WCF ignores the message body to improve performance.</span></span> <span data-ttu-id="96239-147">Pokud chcete filtrovat podle obsahu těla, můžete vytvořit vlastní naslouchací proces s filtrem, který to dělá.</span><span class="sxs-lookup"><span data-stu-id="96239-147">If you want to filter based on the content of the body, you can create a custom listener with a filter that does so.</span></span>  
  
 <span data-ttu-id="96239-148">Chcete-li aktivovat trasování zpráv, je nutné vytvořit naslouchací proces trasování.</span><span class="sxs-lookup"><span data-stu-id="96239-148">You need to create a trace listener to activate message tracing.</span></span> <span data-ttu-id="96239-149">Naslouchací proces může být libovolný naslouchací proces, který pracuje s <xref:System.Diagnostics> architekturou trasování.</span><span class="sxs-lookup"><span data-stu-id="96239-149">The listener itself can be any listener that works with the <xref:System.Diagnostics> tracing architecture.</span></span> <span data-ttu-id="96239-150">Následující příklad ukazuje, jak vytvořit takový naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="96239-150">The following example demonstrates how to create such a listener.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="96239-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="96239-151">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="96239-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="96239-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [<span data-ttu-id="96239-153">Konfigurace protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="96239-153">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
