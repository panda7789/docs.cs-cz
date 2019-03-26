---
title: <add> z <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: 1340b70cf4656b764370a14955a2f4d6f6209fe4
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58466020"
---
# <a name="add-of-filters"></a><span data-ttu-id="f9754-102">\<Přidat > z \<filtry ></span><span class="sxs-lookup"><span data-stu-id="f9754-102">\<add> of \<filters></span></span>
<span data-ttu-id="f9754-103">Filtr XPath určující druh zaznamenávané zprávy.</span><span class="sxs-lookup"><span data-stu-id="f9754-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
 <span data-ttu-id="f9754-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f9754-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f9754-105">\<diagnostic></span><span class="sxs-lookup"><span data-stu-id="f9754-105">\<diagnostic></span></span>  
<span data-ttu-id="f9754-106">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="f9754-106">\<messageLogging></span></span>  
<span data-ttu-id="f9754-107">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="f9754-107">\<filters></span></span>  
<span data-ttu-id="f9754-108">\<add></span><span class="sxs-lookup"><span data-stu-id="f9754-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9754-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9754-109">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9754-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f9754-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f9754-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f9754-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9754-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="f9754-112">Attributes</span></span>  
  
|<span data-ttu-id="f9754-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="f9754-113">Attribute</span></span>|<span data-ttu-id="f9754-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f9754-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f9754-115">filtrování</span><span class="sxs-lookup"><span data-stu-id="f9754-115">filter</span></span>|<span data-ttu-id="f9754-116">Řetězec určující dotaz na dokument jazyka XML, definován výrazem jazyka XPath 1.0.</span><span class="sxs-lookup"><span data-stu-id="f9754-116">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="f9754-117">Další informace naleznete v tématu <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="f9754-117">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9754-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f9754-118">Child Elements</span></span>  
 <span data-ttu-id="f9754-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="f9754-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f9754-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f9754-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f9754-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="f9754-121">Element</span></span>|<span data-ttu-id="f9754-122">Popis</span><span class="sxs-lookup"><span data-stu-id="f9754-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9754-123">\<Filtry></span><span class="sxs-lookup"><span data-stu-id="f9754-123">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters.md)|<span data-ttu-id="f9754-124">Obsahuje kolekci filtrů XPath umožňují určit, jaký druh zprávy se protokoluje.</span><span class="sxs-lookup"><span data-stu-id="f9754-124">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9754-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f9754-125">Remarks</span></span>  
 <span data-ttu-id="f9754-126">Filtry se použijí pouze na transportní vrstvě, určené `logMessagesAtTransportLevel` je `true`.</span><span class="sxs-lookup"><span data-stu-id="f9754-126">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="f9754-127">Protokolování úrovně a poškozené zprávy služby nejsou ovlivněny filtry.</span><span class="sxs-lookup"><span data-stu-id="f9754-127">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="f9754-128">Chcete-li přidat filtr do kolekce, použijte `add` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="f9754-128">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="f9754-129">Když jsou definovány jeden nebo více filtrů, jsou protokolovány jen zprávy, které odpovídají alespoň jeden z filtrů.</span><span class="sxs-lookup"><span data-stu-id="f9754-129">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="f9754-130">Pokud není definován žádný filtr, všechny zprávy předávání.</span><span class="sxs-lookup"><span data-stu-id="f9754-130">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="f9754-131">Filtry podporuje úplnou syntaxi XPath a nastavení se použijí v pořadí, ve kterém se zobrazují v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="f9754-131">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="f9754-132">Filtr syntakticky nesprávný výsledkem výjimka v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="f9754-132">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="f9754-133">Následuje příklad, jak nakonfigurovat filtr, který zaznamenává pouze zprávy, které mají oddíl hlavičky SOAP.</span><span class="sxs-lookup"><span data-stu-id="f9754-133">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9754-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9754-134">Example</span></span>  
 <span data-ttu-id="f9754-135">Následuje příklad, jak nakonfigurovat filtr, který zaznamenává pouze zprávy, které mají oddíl hlavičky SOAP.</span><span class="sxs-lookup"><span data-stu-id="f9754-135">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f9754-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9754-136">See also</span></span>
- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="f9754-137">Konfigurace protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="f9754-137">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="f9754-138">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="f9754-138">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
