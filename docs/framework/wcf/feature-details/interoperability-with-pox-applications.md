---
title: Vzájemná spolupráce s aplikacemi POX
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: 7522233723b6b91d5a7b27d3f82ca328e29ce3f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494196"
---
# <a name="interoperability-with-pox-applications"></a><span data-ttu-id="34ce3-102">Vzájemná spolupráce s aplikacemi POX</span><span class="sxs-lookup"><span data-stu-id="34ce3-102">Interoperability with POX Applications</span></span>
<span data-ttu-id="34ce3-103">"Prostý formát XML" aplikacemi (POX) komunikovat nahrazením nezpracovaná zpráv protokolu HTTP, které obsahují pouze data aplikací XML, který není umístěné do obálky protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="34ce3-103">"Plain Old XML" (POX) applications communicate by exchanging raw HTTP messages that contain only XML application data that is not enclosed within a SOAP envelope.</span></span> <span data-ttu-id="34ce3-104">Windows Communication Foundation (WCF) nabízejí služby a klienti, kteří používají POX zprávy.</span><span class="sxs-lookup"><span data-stu-id="34ce3-104">Windows Communication Foundation (WCF) can provide both services and clients that use POX messages.</span></span> <span data-ttu-id="34ce3-105">Ve službě slouží k implementaci služeb, které zveřejňují koncové body pro klienty, například webové prohlížeče a skriptovací jazyky, které odesílat a přijímat zprávy POX WCF.</span><span class="sxs-lookup"><span data-stu-id="34ce3-105">On the service, WCF can be used to implement services that expose endpoints to clients such as Web browsers and scripting languages that send and receive POX messages.</span></span> <span data-ttu-id="34ce3-106">Na straně klienta programovací model WCF slouží k implementaci klientů komunikujících s služeb založených na POX.</span><span class="sxs-lookup"><span data-stu-id="34ce3-106">On the client, the WCF programming model can be used to implement clients that communicate with POX-based services.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34ce3-107">Tento dokument byl původně zapsán pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0.</span><span class="sxs-lookup"><span data-stu-id="34ce3-107">This document was originally written for the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0.</span></span>  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]<span data-ttu-id="34ce3-108"> 3.5 má integrovanou podporu pro práci s aplikacemi POX.</span><span class="sxs-lookup"><span data-stu-id="34ce3-108"> 3.5 has built-in support for working with POX applications.</span></span> <span data-ttu-id="34ce3-109">Další informace najdete v tématu [WCF Web HTTP programovací Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)</span><span class="sxs-lookup"><span data-stu-id="34ce3-109">For more information about see [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)</span></span>  
  
## <a name="pox-programming-with-wcf"></a><span data-ttu-id="34ce3-110">POX programování s použitím technologie WCF</span><span class="sxs-lookup"><span data-stu-id="34ce3-110">POX Programming with WCF</span></span>  
 <span data-ttu-id="34ce3-111">Služby WCF, které komunikují přes protokol HTTP pomocí zprávy POX [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="34ce3-111">WCF services that communicate over HTTP using POX messages use a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
```xml  
<customBinding>  
   <binding name="poxServerBinding">  
       <textMessageEncoding messageVersion="None" />  
       <httpTransport />  
   </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="34ce3-112">Tato vlastní vazby obsahuje dva elementy:</span><span class="sxs-lookup"><span data-stu-id="34ce3-112">This custom binding contains two elements:</span></span>  
  
-   <span data-ttu-id="34ce3-113">[ \<HttpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) a</span><span class="sxs-lookup"><span data-stu-id="34ce3-113">The [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) and</span></span>  
  
-   <span data-ttu-id="34ce3-114">[ \<TextMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="34ce3-114">The [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
 <span data-ttu-id="34ce3-115">Kodér textu zpráv WCF je speciálně nakonfigurovaný na použití standardu <xref:System.ServiceModel.Channels.MessageVersion.None%2A> hodnotu, která umožňuje zpracovat XML zprávy datové části není přicházející uzavřen do obálky protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="34ce3-115">The standard WCF Text Message Encoder is specially configured to use the <xref:System.ServiceModel.Channels.MessageVersion.None%2A> value, which allows it to process XML message payloads that do not arrive wrapped in a SOAP envelope.</span></span>  
  
 <span data-ttu-id="34ce3-116">Klienti WCF, které komunikují přes protokol HTTP pomocí POX zprávy použít vazbu podobné (viz následující imperativní kód).</span><span class="sxs-lookup"><span data-stu-id="34ce3-116">WCF clients that communicate over HTTP using POX messages use a similar binding (shown in the following imperative code).</span></span>  
  
```  
private static Binding CreatePoxBinding()  
{  
    TextMessageEncodingBindingElement encoder =   
    new TextMessageEncodingBindingElement( MessageVersion.None, Encoding.UTF8 );  
    HttpTransportBindingElement transport = new HttpTransportBindingElement();  
    transport.ManualAddressing = true;  
    return new CustomBinding( new BindingElement[] { encoder, transport } );  
}   
```  
  
 <span data-ttu-id="34ce3-117">Protože klienti POX musí explicitně zadat identifikátory URI, na který budou posílat zprávy, se obvykle musíte nakonfigurovat <xref:System.ServiceModel.Channels.HttpTransportBindingElement> na režim ručního adresování nastavením <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> vlastnost `true` v elementu.</span><span class="sxs-lookup"><span data-stu-id="34ce3-117">Because POX clients must explicitly specify the URIs to which they send messages, they usually must configure the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> to a manual addressing mode by setting the <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> property to `true` on the element.</span></span> <span data-ttu-id="34ce3-118">To umožňuje zprávy explicitně používala kódu aplikace a není nutné vytvořit nový <xref:System.ServiceModel.ChannelFactory> pokaždé, když aplikace odešle zprávu do jiný identifikátor URI HTTP.</span><span class="sxs-lookup"><span data-stu-id="34ce3-118">This allows messages to be addressed explicitly by application code and it is not necessary to create a new <xref:System.ServiceModel.ChannelFactory> every time an application sends a message to a different HTTP URI.</span></span>  
  
 <span data-ttu-id="34ce3-119">Protože zprávy POX nepoužívají hlavičky SOAP pro vyjádření protokolu důležité informace, často služby a klienti POX upravit kusy základní požadavek HTTP umožňuje odesílat nebo přijímat zprávy.</span><span class="sxs-lookup"><span data-stu-id="34ce3-119">Because POX messages do not use SOAP headers to convey important protocol information, POX clients and services often must manipulate pieces of the underlying HTTP request used to send or receive a message.</span></span> <span data-ttu-id="34ce3-120">Protokol HTTP specifické informace, jako je záhlaví HTTP a stavové kódy jsou prezentované v programovací model WCF přes dvě třídy:</span><span class="sxs-lookup"><span data-stu-id="34ce3-120">HTTP-specific protocol information such as the HTTP headers and status codes are surfaced in the WCF programming model through two classes:</span></span>  
  
-   <span data-ttu-id="34ce3-121"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, který obsahuje informace o požadavku HTTP, jako je například metoda a požadavek hlavičky HTTP.</span><span class="sxs-lookup"><span data-stu-id="34ce3-121"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, which contains information about the HTTP request, such as the HTTP method and request headers.</span></span>  
  
-   <span data-ttu-id="34ce3-122"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, který obsahuje informace o odpovědi HTTP, například popis stav a kód stavu HTTP, stejně jako všechny hlavičky HTTP odpovědi.</span><span class="sxs-lookup"><span data-stu-id="34ce3-122"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, which contains information about the HTTP response, such as the HTTP status code and status description, as well as any HTTP response headers.</span></span>  
  
 <span data-ttu-id="34ce3-123">Následující příklad kódu ukazuje, jak vytvořit zprávu požadavku HTTP GET, která je určena http://localhost:8100/customers.</span><span class="sxs-lookup"><span data-stu-id="34ce3-123">The following code example shows how to create an HTTP GET request message that is addressed to http://localhost:8100/customers.</span></span>  
  
```  
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );  
request.Headers.To = "http://localhost:8100/customers";  
  
HttpRequestMessageProperty property = new HttpRequestMessageProperty();  
property.Method = "GET";  
property.SuppressEntityBody = true;  
request.Properties.Add( HttpRequestMessageProperty.Name, property );  
```  
  
 <span data-ttu-id="34ce3-124">První, žádost o vyprázdnění <xref:System.ServiceModel.Channels.Message> je vytvořená voláním <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="34ce3-124">First, an empty request <xref:System.ServiceModel.Channels.Message> is created by calling <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span></span> <span data-ttu-id="34ce3-125"><xref:System.ServiceModel.Channels.MessageVersion.None%2A> Parametr se používá k označení, že není požadováno obálku protokolu SOAP a <xref:System.String.Empty> parametr se předává jako akce.</span><span class="sxs-lookup"><span data-stu-id="34ce3-125">The <xref:System.ServiceModel.Channels.MessageVersion.None%2A> parameter is used to indicate that a SOAP envelope is not required and <xref:System.String.Empty> parameter is passed as the Action.</span></span> <span data-ttu-id="34ce3-126">Zpráva požadavku je pak řešit nastavením <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> záhlaví na požadovaný identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="34ce3-126">The request message is then addressed by setting <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> header to the desired URI.</span></span> <span data-ttu-id="34ce3-127">Dále <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> je vytvořena a <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> je nastaven na příkazu HTTP metodu GET a <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> je nastaven na `true` indikující, že by měl v těle odchozí zprávy požadavku HTTP odesílána žádná data.</span><span class="sxs-lookup"><span data-stu-id="34ce3-127">Next, an <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> is created and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> is set to the HTTP verb GET method and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> is set to `true` to indicate that no data should be sent in the body of the outgoing HTTP request message.</span></span> <span data-ttu-id="34ce3-128">Nakonec je do vlastnost požadavku <xref:System.ServiceModel.Channels.Message.Properties%2A> kolekce zprávě požadavku, takže ho mohou mít vliv na to, jak přenos HTTP odešle žádost.</span><span class="sxs-lookup"><span data-stu-id="34ce3-128">Finally, the request property is added to the <xref:System.ServiceModel.Channels.Message.Properties%2A> collection of the request message so it can influence how the HTTP Transport sends the request.</span></span> <span data-ttu-id="34ce3-129">Zpráva je pak budou odeslány přes příslušné instanci <xref:System.ServiceModel.Channels.IRequestChannel>.</span><span class="sxs-lookup"><span data-stu-id="34ce3-129">The message is then ready to be sent over an appropriate instance of the <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span>  
  
 <span data-ttu-id="34ce3-130">Podobné techniky lze ve službě k extrakci <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> ze služby příchozí zprávy a konstrukce odpověď.</span><span class="sxs-lookup"><span data-stu-id="34ce3-130">Similar techniques can be used on the service to extract the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> from an incoming message and construct a response.</span></span>
