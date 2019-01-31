---
title: <add> z <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: 0e42766cd94b58562bc5728d517e65e80f558cda
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55288792"
---
# <a name="add-of-filters"></a><span data-ttu-id="c792b-102">\<Přidat > z \<filtry ></span><span class="sxs-lookup"><span data-stu-id="c792b-102">\<add> of \<filters></span></span>
<span data-ttu-id="c792b-103">Filtr XPath určující druh zaznamenávané zprávy.</span><span class="sxs-lookup"><span data-stu-id="c792b-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
 <span data-ttu-id="c792b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c792b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c792b-105">\<diagnostic></span><span class="sxs-lookup"><span data-stu-id="c792b-105">\<diagnostic></span></span>  
<span data-ttu-id="c792b-106">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="c792b-106">\<messageLogging></span></span>  
<span data-ttu-id="c792b-107">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="c792b-107">\<filters></span></span>  
<span data-ttu-id="c792b-108">\<add></span><span class="sxs-lookup"><span data-stu-id="c792b-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c792b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c792b-109">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c792b-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c792b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c792b-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c792b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c792b-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="c792b-112">Attributes</span></span>  
  
|<span data-ttu-id="c792b-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="c792b-113">Attribute</span></span>|<span data-ttu-id="c792b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c792b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c792b-115">filtrování</span><span class="sxs-lookup"><span data-stu-id="c792b-115">filter</span></span>|<span data-ttu-id="c792b-116">Řetězec určující dotaz na dokument jazyka XML, definován výrazem jazyka XPath 1.0.</span><span class="sxs-lookup"><span data-stu-id="c792b-116">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="c792b-117">Další informace naleznete v tématu <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="c792b-117">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c792b-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c792b-118">Child Elements</span></span>  
 <span data-ttu-id="c792b-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="c792b-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c792b-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c792b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c792b-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="c792b-121">Element</span></span>|<span data-ttu-id="c792b-122">Popis</span><span class="sxs-lookup"><span data-stu-id="c792b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c792b-123">\<Filtry></span><span class="sxs-lookup"><span data-stu-id="c792b-123">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters.md)|<span data-ttu-id="c792b-124">Obsahuje kolekci filtrů XPath umožňují určit, jaký druh zprávy se protokoluje.</span><span class="sxs-lookup"><span data-stu-id="c792b-124">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c792b-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c792b-125">Remarks</span></span>  
 <span data-ttu-id="c792b-126">Filtry se použijí pouze na transportní vrstvě, určené `logMessagesAtTransportLevel` je `true`.</span><span class="sxs-lookup"><span data-stu-id="c792b-126">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="c792b-127">Protokolování úrovně a poškozené zprávy služby nejsou ovlivněny filtry.</span><span class="sxs-lookup"><span data-stu-id="c792b-127">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="c792b-128">Chcete-li přidat filtr do kolekce, použijte `add` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="c792b-128">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="c792b-129">Když jsou definovány jeden nebo více filtrů, jsou protokolovány jen zprávy, které odpovídají alespoň jeden z filtrů.</span><span class="sxs-lookup"><span data-stu-id="c792b-129">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="c792b-130">Pokud není definován žádný filtr, všechny zprávy předávání.</span><span class="sxs-lookup"><span data-stu-id="c792b-130">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="c792b-131">Filtry podporuje úplnou syntaxi XPath a nastavení se použijí v pořadí, ve kterém se zobrazují v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="c792b-131">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="c792b-132">Filtr syntakticky nesprávný výsledkem výjimka v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="c792b-132">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="c792b-133">Následuje příklad, jak nakonfigurovat filtr, který zaznamenává pouze zprávy, které mají oddíl hlavičky SOAP.</span><span class="sxs-lookup"><span data-stu-id="c792b-133">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c792b-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="c792b-134">Example</span></span>  
 <span data-ttu-id="c792b-135">Následuje příklad, jak nakonfigurovat filtr, který zaznamenává pouze zprávy, které mají oddíl hlavičky SOAP.</span><span class="sxs-lookup"><span data-stu-id="c792b-135">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c792b-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c792b-136">See also</span></span>
- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="c792b-137">Konfigurace protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="c792b-137">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="c792b-138">Konfigurace protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="c792b-138">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="c792b-139">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="c792b-139">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
