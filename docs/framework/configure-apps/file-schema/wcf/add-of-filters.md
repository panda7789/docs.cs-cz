---
title: <add> z <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: 280c516b17a133930bc4b6621a8c9bc7f4781085
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850560"
---
# <a name="add-of-filters"></a><span data-ttu-id="6eb6f-102">\<Přidat > \<filtrů ></span><span class="sxs-lookup"><span data-stu-id="6eb6f-102">\<add> of \<filters></span></span>
<span data-ttu-id="6eb6f-103">Filtr XPath určující druh zprávy, která má být zaznamenána.</span><span class="sxs-lookup"><span data-stu-id="6eb6f-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
<span data-ttu-id="6eb6f-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6eb6f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6eb6f-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6eb6f-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6eb6f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> diagnostiky**](diagnostics.md)</span><span class="sxs-lookup"><span data-stu-id="6eb6f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)</span></span>\
<span data-ttu-id="6eb6f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<messageLogging >** ](messagelogging.md)</span><span class="sxs-lookup"><span data-stu-id="6eb6f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<messageLogging>**](messagelogging.md)</span></span>\
<span data-ttu-id="6eb6f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> filtrů**](filters.md)</span><span class="sxs-lookup"><span data-stu-id="6eb6f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters.md)</span></span>\
<span data-ttu-id="6eb6f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**</span><span class="sxs-lookup"><span data-stu-id="6eb6f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eb6f-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6eb6f-110">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6eb6f-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6eb6f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6eb6f-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6eb6f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6eb6f-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="6eb6f-113">Attributes</span></span>  
  
|<span data-ttu-id="6eb6f-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="6eb6f-114">Attribute</span></span>|<span data-ttu-id="6eb6f-115">Popis</span><span class="sxs-lookup"><span data-stu-id="6eb6f-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6eb6f-116">filtrování</span><span class="sxs-lookup"><span data-stu-id="6eb6f-116">filter</span></span>|<span data-ttu-id="6eb6f-117">Řetězec, který určuje dotaz na dokumentu XML, který je definován výrazem XPath 1,0.</span><span class="sxs-lookup"><span data-stu-id="6eb6f-117">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="6eb6f-118">Další informace naleznete v tématu <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="6eb6f-118">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6eb6f-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6eb6f-119">Child Elements</span></span>  
 <span data-ttu-id="6eb6f-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="6eb6f-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6eb6f-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6eb6f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6eb6f-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="6eb6f-122">Element</span></span>|<span data-ttu-id="6eb6f-123">Popis</span><span class="sxs-lookup"><span data-stu-id="6eb6f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6eb6f-124">\<Filtry></span><span class="sxs-lookup"><span data-stu-id="6eb6f-124">\<filters></span></span>](filters.md)|<span data-ttu-id="6eb6f-125">Obsahuje kolekci filtrů XPath používaných k řízení toho, jaký druh zprávy je protokolován.</span><span class="sxs-lookup"><span data-stu-id="6eb6f-125">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6eb6f-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6eb6f-126">Remarks</span></span>  
 <span data-ttu-id="6eb6f-127">Filtry se aplikují jenom na transportní vrstvě, kterou `logMessagesAtTransportLevel` `true`určuje.</span><span class="sxs-lookup"><span data-stu-id="6eb6f-127">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="6eb6f-128">Filtry neovlivní úroveň služeb a nesprávně přihlašování zpráv.</span><span class="sxs-lookup"><span data-stu-id="6eb6f-128">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="6eb6f-129">Chcete-li přidat filtr do kolekce, použijte `add` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="6eb6f-129">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="6eb6f-130">Při definování jednoho nebo více filtrů jsou protokolovány pouze zprávy, které odpovídají alespoň jednomu z filtrů.</span><span class="sxs-lookup"><span data-stu-id="6eb6f-130">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="6eb6f-131">Pokud není definován žádný filtr, všechny zprávy procházejí.</span><span class="sxs-lookup"><span data-stu-id="6eb6f-131">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="6eb6f-132">Filtry podporují úplnou syntaxi XPath a jsou aplikovány v pořadí, v jakém jsou uvedeny v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="6eb6f-132">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="6eb6f-133">Syntakticky nesprávný filtr má za následek výjimku konfigurace.</span><span class="sxs-lookup"><span data-stu-id="6eb6f-133">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="6eb6f-134">Následuje příklad, jak nakonfigurovat filtr, který zaznamenává pouze zprávy, které mají hlavičku SOAP.</span><span class="sxs-lookup"><span data-stu-id="6eb6f-134">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6eb6f-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="6eb6f-135">Example</span></span>  
 <span data-ttu-id="6eb6f-136">Následuje příklad, jak nakonfigurovat filtr, který zaznamenává pouze zprávy, které mají hlavičku SOAP.</span><span class="sxs-lookup"><span data-stu-id="6eb6f-136">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6eb6f-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6eb6f-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="6eb6f-138">Konfigurace protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="6eb6f-138">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="6eb6f-139">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="6eb6f-139">\<messageLogging></span></span>](messagelogging.md)
