---
title: <add> z <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: 280c516b17a133930bc4b6621a8c9bc7f4781085
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850560"
---
# <a name="add-of-filters"></a><span data-ttu-id="c2481-102">\<add> z \<filters></span><span class="sxs-lookup"><span data-stu-id="c2481-102">\<add> of \<filters></span></span>
<span data-ttu-id="c2481-103">Filtr XPath určující druh zprávy, která má být zaznamenána.</span><span class="sxs-lookup"><span data-stu-id="c2481-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<messageLogging>**](messagelogging.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="c2481-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2481-104">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2481-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c2481-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c2481-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c2481-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2481-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="c2481-107">Attributes</span></span>  
  
|<span data-ttu-id="c2481-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="c2481-108">Attribute</span></span>|<span data-ttu-id="c2481-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c2481-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c2481-110">filtrování</span><span class="sxs-lookup"><span data-stu-id="c2481-110">filter</span></span>|<span data-ttu-id="c2481-111">Řetězec, který určuje dotaz na dokumentu XML, který je definován výrazem XPath 1,0.</span><span class="sxs-lookup"><span data-stu-id="c2481-111">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="c2481-112">Další informace naleznete v tématu <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="c2481-112">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2481-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c2481-113">Child Elements</span></span>  
 <span data-ttu-id="c2481-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="c2481-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c2481-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c2481-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c2481-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="c2481-116">Element</span></span>|<span data-ttu-id="c2481-117">Description</span><span class="sxs-lookup"><span data-stu-id="c2481-117">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters.md)|<span data-ttu-id="c2481-118">Obsahuje kolekci filtrů XPath používaných k řízení toho, jaký druh zprávy je protokolován.</span><span class="sxs-lookup"><span data-stu-id="c2481-118">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2481-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2481-119">Remarks</span></span>  
 <span data-ttu-id="c2481-120">Filtry se aplikují jenom na transportní vrstvě, kterou Určuje `logMessagesAtTransportLevel` `true` .</span><span class="sxs-lookup"><span data-stu-id="c2481-120">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="c2481-121">Filtry neovlivní úroveň služeb a nesprávně přihlašování zpráv.</span><span class="sxs-lookup"><span data-stu-id="c2481-121">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="c2481-122">Chcete-li přidat filtr do kolekce, použijte `add` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="c2481-122">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="c2481-123">Při definování jednoho nebo více filtrů jsou protokolovány pouze zprávy, které odpovídají alespoň jednomu z filtrů.</span><span class="sxs-lookup"><span data-stu-id="c2481-123">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="c2481-124">Pokud není definován žádný filtr, všechny zprávy procházejí.</span><span class="sxs-lookup"><span data-stu-id="c2481-124">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="c2481-125">Filtry podporují úplnou syntaxi XPath a jsou aplikovány v pořadí, v jakém jsou uvedeny v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="c2481-125">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="c2481-126">Syntakticky nesprávný filtr má za následek výjimku konfigurace.</span><span class="sxs-lookup"><span data-stu-id="c2481-126">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="c2481-127">Následuje příklad, jak nakonfigurovat filtr, který zaznamenává pouze zprávy, které mají hlavičku SOAP.</span><span class="sxs-lookup"><span data-stu-id="c2481-127">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2481-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2481-128">Example</span></span>  
 <span data-ttu-id="c2481-129">Následuje příklad, jak nakonfigurovat filtr, který zaznamenává pouze zprávy, které mají hlavičku SOAP.</span><span class="sxs-lookup"><span data-stu-id="c2481-129">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c2481-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2481-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="c2481-131">Konfigurace protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="c2481-131">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging>](messagelogging.md)
