---
title: '&lt;messageLogging&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d2febd8582ded47827794762bf0fb842c8131666
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltmessagelogginggt"></a><span data-ttu-id="1d85d-102">&lt;messageLogging&gt;</span><span class="sxs-lookup"><span data-stu-id="1d85d-102">&lt;messageLogging&gt;</span></span>
<span data-ttu-id="1d85d-103">Tento element definuje nastavení pro protokolování zpráv možnosti Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1d85d-103">This element defines the settings for the message-logging capabilities of Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="1d85d-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1d85d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1d85d-105">\<diagnostické ></span><span class="sxs-lookup"><span data-stu-id="1d85d-105">\<diagnostic></span></span>  
<span data-ttu-id="1d85d-106">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="1d85d-106">\<messageLogging></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d85d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d85d-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <messageLogging logEntireMessage="Boolean"  
          logMalformedMessages="Boolean"  
          logMessagesAtServiceLevel="Boolean"  
          logMessagesAtTransportLevel="Boolean"  
                    maxMessagesToLog="Integer"  
          maxSizeOfMessageToLog="Integer" >  
          <filters>  
                            <clear />  
          </filters>  
       </messageLogging>  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d85d-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1d85d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1d85d-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1d85d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d85d-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="1d85d-110">Attributes</span></span>  
  
|<span data-ttu-id="1d85d-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="1d85d-111">Attribute</span></span>|<span data-ttu-id="1d85d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="1d85d-112">Description</span></span>|  
|---------------|-----------------|  
|`logEntireMessage`|<span data-ttu-id="1d85d-113">Logická hodnota, která určuje, zda je zaznamenána celé zprávy (záhlaví zprávy a text).</span><span class="sxs-lookup"><span data-stu-id="1d85d-113">A Boolean value that specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="1d85d-114">Výchozí hodnota je `false`, což znamená, že pouze záhlaví zprávy přihlášen.</span><span class="sxs-lookup"><span data-stu-id="1d85d-114">The default is `false`, which means that only the message header is logged.</span></span> <span data-ttu-id="1d85d-115">Toto nastavení ovlivňuje všechny úrovně protokolování zpráv (service, přenos a chybná).</span><span class="sxs-lookup"><span data-stu-id="1d85d-115">This setting affects all message logging levels (service, transport, and malformed).</span></span>|  
|`logMalformedMessages`|<span data-ttu-id="1d85d-116">Logická hodnota, která určuje, zda mají být protokolovány poškozených zpráv.</span><span class="sxs-lookup"><span data-stu-id="1d85d-116">A Boolean value that specifies whether malformed messages are logged.</span></span> <span data-ttu-id="1d85d-117">Poškozených zpráv nepočítá `maxMessagesToLog`.</span><span class="sxs-lookup"><span data-stu-id="1d85d-117">Malformed messages do not count toward the `maxMessagesToLog`.</span></span> <span data-ttu-id="1d85d-118">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="1d85d-118">The default is `false`.</span></span>|  
|`logMessagesAtServiceLevel`|<span data-ttu-id="1d85d-119">Logická hodnota, která určuje, zda jsou zprávy nalezeny na úrovni služby (před šifrování a přenosu související transformací).</span><span class="sxs-lookup"><span data-stu-id="1d85d-119">A Boolean value that specifies whether messages are traced at the service level (before encryption- and transport-related transforms).</span></span> <span data-ttu-id="1d85d-120">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="1d85d-120">The default is `false`.</span></span>|  
|`logMessagesAtTransportLevel`|<span data-ttu-id="1d85d-121">Logická hodnota, která určuje, zda jsou zprávy nalezeny na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="1d85d-121">A Boolean value that specifies whether messages are traced at the transport level.</span></span> <span data-ttu-id="1d85d-122">Jsou použity žádné filtry zadané v konfiguračním souboru, a budou trasovány pouze zprávy, které splňují podmínky filtrů.</span><span class="sxs-lookup"><span data-stu-id="1d85d-122">Any filters specified in the config file are applied, and only messages that match the filters are traced.</span></span> <span data-ttu-id="1d85d-123">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="1d85d-123">The default is `false`.</span></span>|  
|`maxMessagesToLog`|<span data-ttu-id="1d85d-124">Kladné celé číslo, které určuje maximální počet zpráv do protokolu.</span><span class="sxs-lookup"><span data-stu-id="1d85d-124">A positive integer that specifies the maximum number of messages to log.</span></span> <span data-ttu-id="1d85d-125">Výchozí hodnota je 1 000.</span><span class="sxs-lookup"><span data-stu-id="1d85d-125">The default is 1000.</span></span>|  
|`maxSizeOfMessageToLog`|<span data-ttu-id="1d85d-126">Kladné celé číslo, které určuje maximální velikost v bajtech zprávy do protokolu.</span><span class="sxs-lookup"><span data-stu-id="1d85d-126">A positive integer that specifies the maximum size, in bytes, of a message to log.</span></span> <span data-ttu-id="1d85d-127">Zprávy, které jsou větší než limit se nebudou protokolovat.</span><span class="sxs-lookup"><span data-stu-id="1d85d-127">Messages larger than the limit will not be logged.</span></span> <span data-ttu-id="1d85d-128">Toto nastavení ovlivňuje všechny úrovně trasování.</span><span class="sxs-lookup"><span data-stu-id="1d85d-128">This setting affects all trace levels.</span></span> <span data-ttu-id="1d85d-129">Výchozí hodnota je 262144(0x4000).</span><span class="sxs-lookup"><span data-stu-id="1d85d-129">The default is 262144(0x4000).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d85d-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1d85d-130">Child Elements</span></span>  
  
|<span data-ttu-id="1d85d-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="1d85d-131">Element</span></span>|<span data-ttu-id="1d85d-132">Popis</span><span class="sxs-lookup"><span data-stu-id="1d85d-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1d85d-133">filtry</span><span class="sxs-lookup"><span data-stu-id="1d85d-133">filters</span></span>|<span data-ttu-id="1d85d-134">`filters` Element obsahuje kolekci filtrů XPath.</span><span class="sxs-lookup"><span data-stu-id="1d85d-134">The `filters` element holds a collection of XPath filters.</span></span> <span data-ttu-id="1d85d-135">Když je povoleno protokolování přenosu zpráv (`logMessagesAtTransportLevel` je `true`), bude do protokolu pouze zprávy odpovídající filtry.</span><span class="sxs-lookup"><span data-stu-id="1d85d-135">When transport message logging is enabled (`logMessagesAtTransportLevel` is `true`), only messages matching the filters will be logged.</span></span><br /><br /> <span data-ttu-id="1d85d-136">Filtry se použijí jenom v přenosové vrstvě.</span><span class="sxs-lookup"><span data-stu-id="1d85d-136">Filters are applied only at the transport layer.</span></span> <span data-ttu-id="1d85d-137">Protokolování úrovně a poškozených zpráv služby nemá vliv filtry.</span><span class="sxs-lookup"><span data-stu-id="1d85d-137">Service level and malformed message logging are not affected by filters.</span></span><br /><br /> <span data-ttu-id="1d85d-138">Atribut pouze pro tento element `filter`, je třída XpathFilter.</span><span class="sxs-lookup"><span data-stu-id="1d85d-138">The only attribute for this element, `filter`, is an XpathFilter.</span></span><br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a><span data-ttu-id="1d85d-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1d85d-139">Parent Elements</span></span>  
  
|<span data-ttu-id="1d85d-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="1d85d-140">Element</span></span>|<span data-ttu-id="1d85d-141">Popis</span><span class="sxs-lookup"><span data-stu-id="1d85d-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1d85d-142">diagnostika</span><span class="sxs-lookup"><span data-stu-id="1d85d-142">diagnostics</span></span>|<span data-ttu-id="1d85d-143">Definuje nastavení WCF pro modul runtime kontroly a řízení pro správce.</span><span class="sxs-lookup"><span data-stu-id="1d85d-143">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d85d-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1d85d-144">Remarks</span></span>  
 <span data-ttu-id="1d85d-145">Zprávy se zaznamenávají na třech různých úrovních v zásobníku: service, přenos a je poškozený.</span><span class="sxs-lookup"><span data-stu-id="1d85d-145">Messages are logged at three different levels in the stack: service, transport, and malformed.</span></span> <span data-ttu-id="1d85d-146">Každá úroveň je možné aktivovat samostatně.</span><span class="sxs-lookup"><span data-stu-id="1d85d-146">Each level can be activated separately.</span></span>  
  
 <span data-ttu-id="1d85d-147">Filtry jazyka XPath lze přidat k protokolování konkrétní zpráv na úrovni přenosu a služby.</span><span class="sxs-lookup"><span data-stu-id="1d85d-147">XPath filters can be added to log specific messages at the transport and service levels.</span></span> <span data-ttu-id="1d85d-148">Pokud jsou definovány žádné filtry, jsou protokolovány všechny zprávy.</span><span class="sxs-lookup"><span data-stu-id="1d85d-148">If no filters are defined, all messages are logged.</span></span> <span data-ttu-id="1d85d-149">Filtry se použijí jenom u záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="1d85d-149">Filters are applied only to the headers of the message.</span></span> <span data-ttu-id="1d85d-150">Text se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="1d85d-150">The body is ignored.</span></span> <span data-ttu-id="1d85d-151">WCF ignoruje tělo zprávy ke zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="1d85d-151">WCF ignores the message body to improve performance.</span></span> <span data-ttu-id="1d85d-152">Pokud chcete filtrovat podle obsah textu, můžete vytvořit vlastní naslouchací proces s filtr, který nemá tak.</span><span class="sxs-lookup"><span data-stu-id="1d85d-152">If you want to filter based on the content of the body, you can create a custom listener with a filter that does so.</span></span>  
  
 <span data-ttu-id="1d85d-153">Budete muset vytvořit naslouchací proces trasování aktivujte trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="1d85d-153">You need to create a trace listener to activate message tracing.</span></span> <span data-ttu-id="1d85d-154">Naslouchací proces samotné může být jakékoli naslouchací proces, který funguje s <xref:System.Diagnostics> architektura trasování.</span><span class="sxs-lookup"><span data-stu-id="1d85d-154">The listener itself can be any listener that works with the <xref:System.Diagnostics> tracing architecture.</span></span> <span data-ttu-id="1d85d-155">Následující příklad ukazuje, jak vytvořit naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="1d85d-155">The following example demonstrates how to create such a listener.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
          <source name="System.ServiceModel" switchValue="Verbose">  
              <listeners>  
                    <clear />  
                    <add type="System.Diagnostics.DefaultTraceListener" name="Default"  
                        traceOutputOptions="None" />  
                    <add name="ServiceModel Listener" traceOutputOptions="None" />  
               </listeners>  
        </source>  
            <source name="System.ServiceModel.MessageLogging">  
                <listeners>  
                    <clear />  
                    <add type="System.Diagnostics.DefaultTraceListener" name="Default"  
                        traceOutputOptions="None" />  
                    <add name="MessageLogging Listener" traceOutputOptions="None"/>  
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
  
## <a name="example"></a><span data-ttu-id="1d85d-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d85d-156">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1d85d-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d85d-157">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>  
 [<span data-ttu-id="1d85d-158">Konfigurace protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="1d85d-158">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
