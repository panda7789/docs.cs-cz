---
title: <add> z <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: e7975bea1435abdb77528628e7b96c65a72cbbc2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926688"
---
# <a name="add-of-filters"></a><span data-ttu-id="cbd27-102">\<Přidat > \<filtrů ></span><span class="sxs-lookup"><span data-stu-id="cbd27-102">\<add> of \<filters></span></span>
<span data-ttu-id="cbd27-103">Filtr XPath určující druh zprávy, která má být zaznamenána.</span><span class="sxs-lookup"><span data-stu-id="cbd27-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
 <span data-ttu-id="cbd27-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cbd27-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cbd27-105">\<> diagnostiky</span><span class="sxs-lookup"><span data-stu-id="cbd27-105">\<diagnostic></span></span>  
<span data-ttu-id="cbd27-106">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="cbd27-106">\<messageLogging></span></span>  
<span data-ttu-id="cbd27-107">\<> filtrů</span><span class="sxs-lookup"><span data-stu-id="cbd27-107">\<filters></span></span>  
<span data-ttu-id="cbd27-108">\<add></span><span class="sxs-lookup"><span data-stu-id="cbd27-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbd27-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cbd27-109">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbd27-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cbd27-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cbd27-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cbd27-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbd27-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="cbd27-112">Attributes</span></span>  
  
|<span data-ttu-id="cbd27-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="cbd27-113">Attribute</span></span>|<span data-ttu-id="cbd27-114">Popis</span><span class="sxs-lookup"><span data-stu-id="cbd27-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cbd27-115">filtrování</span><span class="sxs-lookup"><span data-stu-id="cbd27-115">filter</span></span>|<span data-ttu-id="cbd27-116">Řetězec, který určuje dotaz na dokumentu XML, který je definován výrazem XPath 1,0.</span><span class="sxs-lookup"><span data-stu-id="cbd27-116">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="cbd27-117">Další informace naleznete v tématu <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="cbd27-117">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cbd27-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cbd27-118">Child Elements</span></span>  
 <span data-ttu-id="cbd27-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="cbd27-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cbd27-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cbd27-120">Parent Elements</span></span>  
  
|<span data-ttu-id="cbd27-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="cbd27-121">Element</span></span>|<span data-ttu-id="cbd27-122">Popis</span><span class="sxs-lookup"><span data-stu-id="cbd27-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cbd27-123">\<Filtry></span><span class="sxs-lookup"><span data-stu-id="cbd27-123">\<filters></span></span>](filters.md)|<span data-ttu-id="cbd27-124">Obsahuje kolekci filtrů XPath používaných k řízení toho, jaký druh zprávy je protokolován.</span><span class="sxs-lookup"><span data-stu-id="cbd27-124">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbd27-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cbd27-125">Remarks</span></span>  
 <span data-ttu-id="cbd27-126">Filtry se aplikují jenom na transportní vrstvě, kterou `logMessagesAtTransportLevel` `true`určuje.</span><span class="sxs-lookup"><span data-stu-id="cbd27-126">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="cbd27-127">Filtry neovlivní úroveň služeb a nesprávně přihlašování zpráv.</span><span class="sxs-lookup"><span data-stu-id="cbd27-127">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="cbd27-128">Chcete-li přidat filtr do kolekce, použijte `add` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="cbd27-128">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="cbd27-129">Při definování jednoho nebo více filtrů jsou protokolovány pouze zprávy, které odpovídají alespoň jednomu z filtrů.</span><span class="sxs-lookup"><span data-stu-id="cbd27-129">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="cbd27-130">Pokud není definován žádný filtr, všechny zprávy procházejí.</span><span class="sxs-lookup"><span data-stu-id="cbd27-130">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="cbd27-131">Filtry podporují úplnou syntaxi XPath a jsou aplikovány v pořadí, v jakém jsou uvedeny v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="cbd27-131">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="cbd27-132">Syntakticky nesprávný filtr má za následek výjimku konfigurace.</span><span class="sxs-lookup"><span data-stu-id="cbd27-132">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="cbd27-133">Následuje příklad, jak nakonfigurovat filtr, který zaznamenává pouze zprávy, které mají hlavičku SOAP.</span><span class="sxs-lookup"><span data-stu-id="cbd27-133">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbd27-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="cbd27-134">Example</span></span>  
 <span data-ttu-id="cbd27-135">Následuje příklad, jak nakonfigurovat filtr, který zaznamenává pouze zprávy, které mají hlavičku SOAP.</span><span class="sxs-lookup"><span data-stu-id="cbd27-135">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
```xml  
<messageLogging logEntireMessage="true"
                logMalformedMessages="true"
                logMessagesAtServiceLevel="true"
                logMessagesAtTransportLevel="true"
                maxMessagesToLog="420">
  <filters>
    <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
      /soap:Envelope/soap:Headers
    </add>
  </filters>
</messageLogging>
```  
  
## <a name="see-also"></a><span data-ttu-id="cbd27-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cbd27-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="cbd27-137">Konfigurace protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="cbd27-137">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="cbd27-138">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="cbd27-138">\<messageLogging></span></span>](messagelogging.md)
