---
title: Interoperabilita s aplikacemi POX
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: 64a6d850a32b14bc60cd43466e04b53a7a39be81
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579264"
---
# <a name="interoperability-with-pox-applications"></a><span data-ttu-id="a5d48-102">Interoperabilita s aplikacemi POX</span><span class="sxs-lookup"><span data-stu-id="a5d48-102">Interoperability with POX applications</span></span>

<span data-ttu-id="a5d48-103">"Obyčejné staré aplikace XML" (POX) komunikují výměnou nezpracovaných zpráv HTTP, které obsahují jenom data aplikace XML, která nejsou uzavřená v obálce protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="a5d48-103">"Plain Old XML" (POX) applications communicate by exchanging raw HTTP messages that contain only XML application data that is not enclosed within a SOAP envelope.</span></span> <span data-ttu-id="a5d48-104">Windows Communication Foundation (WCF) může poskytovat služby i klienty, kteří používají zprávy POX.</span><span class="sxs-lookup"><span data-stu-id="a5d48-104">Windows Communication Foundation (WCF) can provide both services and clients that use POX messages.</span></span> <span data-ttu-id="a5d48-105">Ve službě lze WCF použít k implementaci služeb, které zpřístupňují koncové body klientům, jako jsou webové prohlížeče a skriptovací jazyky, které odesílají a získávají zprávy POX.</span><span class="sxs-lookup"><span data-stu-id="a5d48-105">On the service, WCF can be used to implement services that expose endpoints to clients such as Web browsers and scripting languages that send and receive POX messages.</span></span> <span data-ttu-id="a5d48-106">Na straně klienta lze použít programovací model WCF k implementaci klientů, kteří komunikují se službami založeným na POX.</span><span class="sxs-lookup"><span data-stu-id="a5d48-106">On the client, the WCF programming model can be used to implement clients that communicate with POX-based services.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a5d48-107">Tento dokument byl původně napsán pro .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="a5d48-107">This document was originally written for the .NET Framework 3.0.</span></span>  <span data-ttu-id="a5d48-108">.NET Framework 3,5 obsahuje integrovanou podporu pro práci s POX aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="a5d48-108">.NET Framework 3.5 has built-in support for working with POX applications.</span></span> <span data-ttu-id="a5d48-109">Další informace najdete v tématu [model programování webového protokolu HTTP WCF](wcf-web-http-programming-model.md).</span><span class="sxs-lookup"><span data-stu-id="a5d48-109">For more information about see [WCF Web HTTP Programming Model](wcf-web-http-programming-model.md).</span></span>
  
## <a name="pox-programming-with-wcf"></a><span data-ttu-id="a5d48-110">POX programování pomocí WCF</span><span class="sxs-lookup"><span data-stu-id="a5d48-110">POX programming with WCF</span></span>

<span data-ttu-id="a5d48-111">Služby WCF, které komunikují přes protokol HTTP pomocí zpráv POX, používají [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="a5d48-111">WCF services that communicate over HTTP using POX messages use a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>

```xml
<customBinding>
   <binding name="poxServerBinding">
       <textMessageEncoding messageVersion="None" />
       <httpTransport />
   </binding>
</customBinding>
```

<span data-ttu-id="a5d48-112">Tato vlastní vazba obsahuje dva prvky:</span><span class="sxs-lookup"><span data-stu-id="a5d48-112">This custom binding contains two elements:</span></span>

- [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md)

- [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md)

<span data-ttu-id="a5d48-113">Standardní kodér textových zpráv WCF je speciálně nakonfigurován tak, aby používal <xref:System.ServiceModel.Channels.MessageVersion.None%2A> hodnotu, což umožňuje zpracovat datové části zpráv XML, které nepřicházejí do obálky protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="a5d48-113">The standard WCF Text Message Encoder is specially configured to use the <xref:System.ServiceModel.Channels.MessageVersion.None%2A> value, which allows it to process XML message payloads that do not arrive wrapped in a SOAP envelope.</span></span>

<span data-ttu-id="a5d48-114">Klienti WCF, kteří komunikují přes HTTP pomocí zpráv POX, používají podobnou vazbu (viz následující imperativní kód).</span><span class="sxs-lookup"><span data-stu-id="a5d48-114">WCF clients that communicate over HTTP using POX messages use a similar binding (shown in the following imperative code).</span></span>

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

<span data-ttu-id="a5d48-115">Vzhledem k tomu, že klienti POX musí explicitně zadat identifikátory URI, na které odesílají zprávy, obvykle musí nakonfigurovat <xref:System.ServiceModel.Channels.HttpTransportBindingElement> režim ruční adresování nastavením vlastnosti na hodnotu <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> `true` elementu.</span><span class="sxs-lookup"><span data-stu-id="a5d48-115">Because POX clients must explicitly specify the URIs to which they send messages, they usually must configure the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> to a manual addressing mode by setting the <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> property to `true` on the element.</span></span> <span data-ttu-id="a5d48-116">To umožňuje, aby zprávy byly explicitně řešeny kódem aplikace a není nutné vytvářet nové, <xref:System.ServiceModel.ChannelFactory> kdykoli aplikace odešle zprávu na jiný identifikátor URI protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="a5d48-116">This allows messages to be addressed explicitly by application code and it is not necessary to create a new <xref:System.ServiceModel.ChannelFactory> every time an application sends a message to a different HTTP URI.</span></span>

<span data-ttu-id="a5d48-117">Vzhledem k tomu, že zprávy POX nepoužívají hlavičky protokolu SOAP k předávání důležitých informací o protokolu, musí klienti a služby POX často manipulovat s částmi základní žádosti HTTP použitou k odeslání nebo přijetí zprávy.</span><span class="sxs-lookup"><span data-stu-id="a5d48-117">Because POX messages do not use SOAP headers to convey important protocol information, POX clients and services often must manipulate pieces of the underlying HTTP request used to send or receive a message.</span></span> <span data-ttu-id="a5d48-118">Informace protokolu specifické pro protokol HTTP, jako jsou hlavičky protokolu HTTP a stavové kódy, jsou umístěny v programovacím modelu WCF prostřednictvím dvou tříd:</span><span class="sxs-lookup"><span data-stu-id="a5d48-118">HTTP-specific protocol information such as the HTTP headers and status codes are surfaced in the WCF programming model through two classes:</span></span>

- <span data-ttu-id="a5d48-119"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, který obsahuje informace o požadavku HTTP, jako je například metoda HTTP a Hlavička požadavku.</span><span class="sxs-lookup"><span data-stu-id="a5d48-119"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, which contains information about the HTTP request, such as the HTTP method and request headers.</span></span>

- <span data-ttu-id="a5d48-120"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, který obsahuje informace o odpovědi HTTP, například stavový kód HTTP a popis stavu a také všechny hlavičky odpovědí HTTP.</span><span class="sxs-lookup"><span data-stu-id="a5d48-120"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, which contains information about the HTTP response, such as the HTTP status code and status description, as well as any HTTP response headers.</span></span>
  
<span data-ttu-id="a5d48-121">Následující příklad kódu ukazuje, jak vytvořit zprávu požadavku HTTP GET, která je adresována na `http://localhost:8100/customers` .</span><span class="sxs-lookup"><span data-stu-id="a5d48-121">The following code example shows how to create an HTTP GET request message that is addressed to `http://localhost:8100/customers`.</span></span>

```csharp
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );
request.Headers.To = "http://localhost:8100/customers";

HttpRequestMessageProperty property = new HttpRequestMessageProperty();
property.Method = "GET";
property.SuppressEntityBody = true;
request.Properties.Add( HttpRequestMessageProperty.Name, property );
```

<span data-ttu-id="a5d48-122">Nejprve je vytvořen prázdný požadavek <xref:System.ServiceModel.Channels.Message> voláním <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29> .</span><span class="sxs-lookup"><span data-stu-id="a5d48-122">First, an empty request <xref:System.ServiceModel.Channels.Message> is created by calling <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span></span> <span data-ttu-id="a5d48-123"><xref:System.ServiceModel.Channels.MessageVersion.None%2A>Parametr se používá k označení, že obálka SOAP není povinná a <xref:System.String.Empty> jako akce se předává parametr.</span><span class="sxs-lookup"><span data-stu-id="a5d48-123">The <xref:System.ServiceModel.Channels.MessageVersion.None%2A> parameter is used to indicate that a SOAP envelope is not required and <xref:System.String.Empty> parameter is passed as the Action.</span></span> <span data-ttu-id="a5d48-124">Zpráva s požadavkem se pak řeší nastavením <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> hlavičky na požadovaný identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="a5d48-124">The request message is then addressed by setting <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> header to the desired URI.</span></span> <span data-ttu-id="a5d48-125">Dále <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> je vytvořena a je nastavena na <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> metodu Get příkazu HTTP a <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> je nastavena na hodnotu `true` , která označuje, že v těle zprávy odchozího požadavku HTTP by neměly být odesílána žádná data.</span><span class="sxs-lookup"><span data-stu-id="a5d48-125">Next, an <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> is created and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> is set to the HTTP verb GET method and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> is set to `true` to indicate that no data should be sent in the body of the outgoing HTTP request message.</span></span> <span data-ttu-id="a5d48-126">Nakonec se do kolekce zprávy požadavku přidá vlastnost Request <xref:System.ServiceModel.Channels.Message.Properties%2A> , aby mohla ovlivnit, jak přenos HTTP posílá požadavek.</span><span class="sxs-lookup"><span data-stu-id="a5d48-126">Finally, the request property is added to the <xref:System.ServiceModel.Channels.Message.Properties%2A> collection of the request message so it can influence how the HTTP Transport sends the request.</span></span> <span data-ttu-id="a5d48-127">Zpráva je pak připravena k odeslání prostřednictvím vhodné instance <xref:System.ServiceModel.Channels.IRequestChannel> .</span><span class="sxs-lookup"><span data-stu-id="a5d48-127">The message is then ready to be sent over an appropriate instance of the <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span>

<span data-ttu-id="a5d48-128">Podobné techniky lze použít na službu k extrakci <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> z příchozí zprávy a vytvoření odpovědi.</span><span class="sxs-lookup"><span data-stu-id="a5d48-128">Similar techniques can be used on the service to extract the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> from an incoming message and construct a response.</span></span>
