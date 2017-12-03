---
title: "&lt;add&gt; – &lt;filters&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ff083cfbcdfa772bb5904f4311d95e399c22c97e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltfiltersgt"></a><span data-ttu-id="584dc-102">&lt;add&gt; – &lt;filters&gt;</span><span class="sxs-lookup"><span data-stu-id="584dc-102">&lt;add&gt; of &lt;filters&gt;</span></span>
<span data-ttu-id="584dc-103">Filtr XPath, který určuje typ zprávy do protokolu.</span><span class="sxs-lookup"><span data-stu-id="584dc-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
 <span data-ttu-id="584dc-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="584dc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="584dc-105">\<diagnostické ></span><span class="sxs-lookup"><span data-stu-id="584dc-105">\<diagnostic></span></span>  
<span data-ttu-id="584dc-106">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="584dc-106">\<messageLogging></span></span>  
<span data-ttu-id="584dc-107">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="584dc-107">\<filters></span></span>  
<span data-ttu-id="584dc-108">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="584dc-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="584dc-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="584dc-109">Syntax</span></span>  
  
```xml  
<filters>  
   <add filter="String"/>  
</filters>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="584dc-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="584dc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="584dc-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="584dc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="584dc-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="584dc-112">Attributes</span></span>  
  
|<span data-ttu-id="584dc-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="584dc-113">Attribute</span></span>|<span data-ttu-id="584dc-114">Popis</span><span class="sxs-lookup"><span data-stu-id="584dc-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="584dc-115">filtrování</span><span class="sxs-lookup"><span data-stu-id="584dc-115">filter</span></span>|<span data-ttu-id="584dc-116">Řetězec, který určuje dotazu v dokumentu XML definované výraz XPath 1.0.</span><span class="sxs-lookup"><span data-stu-id="584dc-116">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="584dc-117">Další informace naleznete v tématu <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="584dc-117">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="584dc-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="584dc-118">Child Elements</span></span>  
 <span data-ttu-id="584dc-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="584dc-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="584dc-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="584dc-120">Parent Elements</span></span>  
  
|<span data-ttu-id="584dc-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="584dc-121">Element</span></span>|<span data-ttu-id="584dc-122">Popis</span><span class="sxs-lookup"><span data-stu-id="584dc-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="584dc-123">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="584dc-123">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters.md)|<span data-ttu-id="584dc-124">Obsahuje kolekci filtrů XPath použít k řízení, jaký typ zprávy přihlášen.</span><span class="sxs-lookup"><span data-stu-id="584dc-124">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="584dc-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="584dc-125">Remarks</span></span>  
 <span data-ttu-id="584dc-126">Filtry se použijí jenom v přenosové vrstvě určeného `logMessagesAtTransportLevel` je `true`.</span><span class="sxs-lookup"><span data-stu-id="584dc-126">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="584dc-127">Protokolování úrovně a poškozených zpráv služby nemá vliv filtry.</span><span class="sxs-lookup"><span data-stu-id="584dc-127">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="584dc-128">Chcete-li přidat filtr do kolekce, použijte `add` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="584dc-128">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="584dc-129">Když jsou definovány jeden nebo více filtrů, jsou protokolovány pouze zprávy, které odpovídají alespoň jeden z filtrů.</span><span class="sxs-lookup"><span data-stu-id="584dc-129">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="584dc-130">Pokud je definován žádný filtr, všechny zprávy předávat.</span><span class="sxs-lookup"><span data-stu-id="584dc-130">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="584dc-131">Filtry podporovat úplnou syntaxí XPath a aplikují v pořadí, ve kterém se zobrazují v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="584dc-131">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="584dc-132">Správnou syntaxi filtr výsledkem výjimka v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="584dc-132">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="584dc-133">Následuje příklad, jak nakonfigurovat filtr, který zaznamenává jen zprávy, které máte oddíl hlavičky SOAP.</span><span class="sxs-lookup"><span data-stu-id="584dc-133">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="584dc-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="584dc-134">Example</span></span>  
 <span data-ttu-id="584dc-135">Následuje příklad, jak nakonfigurovat filtr, který zaznamenává jen zprávy, které máte oddíl hlavičky SOAP.</span><span class="sxs-lookup"><span data-stu-id="584dc-135">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
```xml  
<messageLogging logEntireMessage="true"  
     logMalformedMessages="true" logMessagesAtServiceLevel="true"  
     logMessagesAtTransportLevel="true" maxMessagesToLog="420">  
     <filters>  
        <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">  
                        /soap:Envelope/soap:Headers  
        </add>  
     </filters>  
</messageLogging>  
```  
  
## <a name="see-also"></a><span data-ttu-id="584dc-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="584dc-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>  
 <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>  
 [<span data-ttu-id="584dc-137">Konfigurace protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="584dc-137">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
 [<span data-ttu-id="584dc-138">Konfigurace protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="584dc-138">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
 [<span data-ttu-id="584dc-139">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="584dc-139">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
