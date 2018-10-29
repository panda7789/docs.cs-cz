---
title: Vzájemná funkční spolupráce s aplikacemi POX
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: b7fdb4e16bce52025515ced065d0f48cffb7fa3f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192639"
---
# <a name="interoperability-with-pox-applications"></a><span data-ttu-id="9bf09-102">Vzájemná funkční spolupráce s aplikacemi POX</span><span class="sxs-lookup"><span data-stu-id="9bf09-102">Interoperability with POX applications</span></span>

<span data-ttu-id="9bf09-103">"Plain Old XML" (POX) aplikace komunikovat výměnou nezpracované zprávy protokolu HTTP, které obsahují pouze data aplikací XML, která není uzavřen v rámci obálky protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="9bf09-103">"Plain Old XML" (POX) applications communicate by exchanging raw HTTP messages that contain only XML application data that is not enclosed within a SOAP envelope.</span></span> <span data-ttu-id="9bf09-104">Windows Communication Foundation (WCF) můžete poskytovat služby a klienti, kteří používají POX zprávy.</span><span class="sxs-lookup"><span data-stu-id="9bf09-104">Windows Communication Foundation (WCF) can provide both services and clients that use POX messages.</span></span> <span data-ttu-id="9bf09-105">Ve službě je možné k implementaci služeb, které zpřístupňují koncové body pro klienty, například webových prohlížečů a skriptovací jazyky, které odesílání a příjem zpráv POX WCF.</span><span class="sxs-lookup"><span data-stu-id="9bf09-105">On the service, WCF can be used to implement services that expose endpoints to clients such as Web browsers and scripting languages that send and receive POX messages.</span></span> <span data-ttu-id="9bf09-106">Na straně klienta je možné implementovat klienty, kteří komunikují se službami na základě POX programovacího modelu WCF.</span><span class="sxs-lookup"><span data-stu-id="9bf09-106">On the client, the WCF programming model can be used to implement clients that communicate with POX-based services.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9bf09-107">Tento dokument byl původně zapsán pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0.</span><span class="sxs-lookup"><span data-stu-id="9bf09-107">This document was originally written for the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0.</span></span>  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] <span data-ttu-id="9bf09-108">3.5 obsahuje integrovanou podporu pro práci s aplikacemi POX.</span><span class="sxs-lookup"><span data-stu-id="9bf09-108">3.5 has built-in support for working with POX applications.</span></span> <span data-ttu-id="9bf09-109">Další informace o najdete v tématu [WCF Web HTTP programovací Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).</span><span class="sxs-lookup"><span data-stu-id="9bf09-109">For more information about see [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).</span></span>
  
## <a name="pox-programming-with-wcf"></a><span data-ttu-id="9bf09-110">POX programování s použitím technologie WCF</span><span class="sxs-lookup"><span data-stu-id="9bf09-110">POX programming with WCF</span></span>

<span data-ttu-id="9bf09-111">Služby WCF, které komunikují prostřednictvím protokolu HTTP použijte POX zprávy [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="9bf09-111">WCF services that communicate over HTTP using POX messages use a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>

```xml
<customBinding>
   <binding name="poxServerBinding">
       <textMessageEncoding messageVersion="None" />
       <httpTransport />
   </binding>
</customBinding>
```

<span data-ttu-id="9bf09-112">Tato vlastní vazba obsahuje dva prvky:</span><span class="sxs-lookup"><span data-stu-id="9bf09-112">This custom binding contains two elements:</span></span>

- [<span data-ttu-id="9bf09-113">\<httpTransport ></span><span class="sxs-lookup"><span data-stu-id="9bf09-113">\<httpTransport></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)

- [<span data-ttu-id="9bf09-114">\<textMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="9bf09-114">\<textMessageEncoding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)

<span data-ttu-id="9bf09-115">Standardní kodér textu zprávy WCF je speciálně nakonfigurován pro použití <xref:System.ServiceModel.Channels.MessageVersion.None%2A> hodnotu, která umožňuje zpracování XML zprávy datových částí, které přicházejí nejsou zabaleny v obálce SOAP.</span><span class="sxs-lookup"><span data-stu-id="9bf09-115">The standard WCF Text Message Encoder is specially configured to use the <xref:System.ServiceModel.Channels.MessageVersion.None%2A> value, which allows it to process XML message payloads that do not arrive wrapped in a SOAP envelope.</span></span>

<span data-ttu-id="9bf09-116">Klienti WCF, které komunikují prostřednictvím protokolu HTTP POX zprávy použijte podobně jako vazbu (viz následující imperativního kódu).</span><span class="sxs-lookup"><span data-stu-id="9bf09-116">WCF clients that communicate over HTTP using POX messages use a similar binding (shown in the following imperative code).</span></span>

```csharp
private static Binding CreatePoxBinding()
{
    TextMessageEncodingBindingElement encoder =
        new TextMessageEncodingBindingElement( MessageVersion.None, Encoding.UTF8 );
    HttpTransportBindingElement transport = new HttpTransportBindingElement();
    transport.ManualAddressing = true;
    return new CustomBinding( new BindingElement[] { encoder, transport } );
}
```

<span data-ttu-id="9bf09-117">Vzhledem k tomu POX klienty musíte explicitně zadat identifikátory URI, na který odesílají zprávy, se obvykle musí nakonfigurovat <xref:System.ServiceModel.Channels.HttpTransportBindingElement> k ruční režim adresování tak, že nastavíte <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> vlastnost `true` u elementu.</span><span class="sxs-lookup"><span data-stu-id="9bf09-117">Because POX clients must explicitly specify the URIs to which they send messages, they usually must configure the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> to a manual addressing mode by setting the <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> property to `true` on the element.</span></span> <span data-ttu-id="9bf09-118">To umožňuje zprávy bylo nutné řešit explicitně kód aplikace a není nutné vytvořit novou <xref:System.ServiceModel.ChannelFactory> pokaždé, když aplikace odešle zprávu do jiný identifikátor URI HTTP.</span><span class="sxs-lookup"><span data-stu-id="9bf09-118">This allows messages to be addressed explicitly by application code and it is not necessary to create a new <xref:System.ServiceModel.ChannelFactory> every time an application sends a message to a different HTTP URI.</span></span>

<span data-ttu-id="9bf09-119">Protože POX zprávy nepoužívejte k předání informací důležité protokolu SOAP záhlaví, POX klienty a služby často manipulovat kusy podkladový požadavek HTTP, který se použije k odeslání nebo přijetí zprávy.</span><span class="sxs-lookup"><span data-stu-id="9bf09-119">Because POX messages do not use SOAP headers to convey important protocol information, POX clients and services often must manipulate pieces of the underlying HTTP request used to send or receive a message.</span></span> <span data-ttu-id="9bf09-120">Protokol HTTP konkrétní informace, jako jsou hlavičky protokolu HTTP a stavové kódy jsou prezentované v programovacího modelu WCF pomocí dvou tříd:</span><span class="sxs-lookup"><span data-stu-id="9bf09-120">HTTP-specific protocol information such as the HTTP headers and status codes are surfaced in the WCF programming model through two classes:</span></span>

- <span data-ttu-id="9bf09-121"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, který obsahuje informace o požadavku HTTP, jako jsou metody a žádost o hlavičky protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="9bf09-121"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, which contains information about the HTTP request, such as the HTTP method and request headers.</span></span>

- <span data-ttu-id="9bf09-122"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, který obsahuje informace odpovědi HTTP, jako je například popis stavu HTTP kódu a stav, stejně jako všechny hlavičky odpovědí HTTP.</span><span class="sxs-lookup"><span data-stu-id="9bf09-122"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, which contains information about the HTTP response, such as the HTTP status code and status description, as well as any HTTP response headers.</span></span>
  
<span data-ttu-id="9bf09-123">Následující příklad kódu ukazuje, jak vytvořit požadavku HTTP GET, adresovanou `http://localhost:8100/customers`.</span><span class="sxs-lookup"><span data-stu-id="9bf09-123">The following code example shows how to create an HTTP GET request message that is addressed to `http://localhost:8100/customers`.</span></span>

```csharp
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );
request.Headers.To = "http://localhost:8100/customers";

HttpRequestMessageProperty property = new HttpRequestMessageProperty();
property.Method = "GET";
property.SuppressEntityBody = true;
request.Properties.Add( HttpRequestMessageProperty.Name, property );
```

<span data-ttu-id="9bf09-124">První, žádost o vyprázdnění <xref:System.ServiceModel.Channels.Message> je vytvořen zavoláním <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="9bf09-124">First, an empty request <xref:System.ServiceModel.Channels.Message> is created by calling <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span></span> <span data-ttu-id="9bf09-125"><xref:System.ServiceModel.Channels.MessageVersion.None%2A> Parametr se používá k označení, že není potřeba obálku protokolu SOAP a <xref:System.String.Empty> parametr se předává jako akce.</span><span class="sxs-lookup"><span data-stu-id="9bf09-125">The <xref:System.ServiceModel.Channels.MessageVersion.None%2A> parameter is used to indicate that a SOAP envelope is not required and <xref:System.String.Empty> parameter is passed as the Action.</span></span> <span data-ttu-id="9bf09-126">Zprávy s požadavkem je pak určena nastavením <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> záhlaví na požadovaný identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="9bf09-126">The request message is then addressed by setting <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> header to the desired URI.</span></span> <span data-ttu-id="9bf09-127">Další <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> se vytvoří a <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> je nastavena na příkaz HTTP GET metody a <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> je nastavena na `true` k označení, že by se posílat žádná data v těle odchozí zpráva požadavku HTTP.</span><span class="sxs-lookup"><span data-stu-id="9bf09-127">Next, an <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> is created and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> is set to the HTTP verb GET method and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> is set to `true` to indicate that no data should be sent in the body of the outgoing HTTP request message.</span></span> <span data-ttu-id="9bf09-128">Nakonec je přidána vlastnost požadavek <xref:System.ServiceModel.Channels.Message.Properties%2A> kolekce zprávy s požadavkem, může ovlivnit, jak přenos pomocí protokolu HTTP odesílá požadavek.</span><span class="sxs-lookup"><span data-stu-id="9bf09-128">Finally, the request property is added to the <xref:System.ServiceModel.Channels.Message.Properties%2A> collection of the request message so it can influence how the HTTP Transport sends the request.</span></span> <span data-ttu-id="9bf09-129">Zprávu je připravený k odeslání přes příslušné instanci <xref:System.ServiceModel.Channels.IRequestChannel>.</span><span class="sxs-lookup"><span data-stu-id="9bf09-129">The message is then ready to be sent over an appropriate instance of the <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span>

<span data-ttu-id="9bf09-130">Podobné techniky slouží ve službě k extrakci <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> z k příchozí zprávě a konstrukce odpověď.</span><span class="sxs-lookup"><span data-stu-id="9bf09-130">Similar techniques can be used on the service to extract the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> from an incoming message and construct a response.</span></span>
