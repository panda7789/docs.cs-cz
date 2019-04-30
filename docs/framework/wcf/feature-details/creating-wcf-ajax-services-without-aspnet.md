---
title: Vytváření služeb WCF AJAX bez ASP.NET
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: 77a850408c3d952dbd4f682ea704d3248ae17c3e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857204"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a><span data-ttu-id="2bd03-102">Vytváření služeb WCF AJAX bez ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2bd03-102">Creating WCF AJAX Services without ASP.NET</span></span>
<span data-ttu-id="2bd03-103">AJAX služba Windows Communication Foundation (WCF) je přístupný z jakékoli stránky webové povolen jazyk JavaScript bez nutnosti technologie ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="2bd03-103">Windows Communication Foundation (WCF) AJAX services can be accessed from any JavaScript-enabled Web page, without requiring ASP.NET AJAX.</span></span> <span data-ttu-id="2bd03-104">Toto téma popisuje postup vytvoření služby WCF.</span><span class="sxs-lookup"><span data-stu-id="2bd03-104">This topic describes how to create such a WCF service.</span></span>  
  
 <span data-ttu-id="2bd03-105">Pokyny týkající se použití WCF pomocí ASP.NET AJAX, naleznete v tématu [vytváření služeb WCF pro ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span><span class="sxs-lookup"><span data-stu-id="2bd03-105">For instructions on using WCF with ASP.NET AJAX, see [Creating WCF Services for ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span></span>  
  
 <span data-ttu-id="2bd03-106">Existují tři části vytváření služeb WCF AJAX:</span><span class="sxs-lookup"><span data-stu-id="2bd03-106">There are three parts to a creating a WCF AJAX service:</span></span>  
  
- <span data-ttu-id="2bd03-107">Vytvoření koncového bodu AJAX, který je přístupný z prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="2bd03-107">Creating an AJAX endpoint that can be accessed from the browser.</span></span>  
  
- <span data-ttu-id="2bd03-108">Vytváří se kontrakt služby kompatibilní s AJAX.</span><span class="sxs-lookup"><span data-stu-id="2bd03-108">Creating an AJAX-compatible service contract.</span></span>  
  
- <span data-ttu-id="2bd03-109">Přístup ke službám WCF AJAX.</span><span class="sxs-lookup"><span data-stu-id="2bd03-109">Accessing WCF AJAX services.</span></span>  
  
## <a name="creating-an-ajax-endpoint"></a><span data-ttu-id="2bd03-110">Vytváří se koncový bod AJAX</span><span class="sxs-lookup"><span data-stu-id="2bd03-110">Creating an AJAX Endpoint</span></span>  
 <span data-ttu-id="2bd03-111">Základní způsob, jak povolit podporu AJAX služba WCF je použít <xref:System.ServiceModel.Activation.WebServiceHostFactory> v souboru SVC přidružená ke službě, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2bd03-111">The most basic way to enable AJAX support in a WCF service is to use the <xref:System.ServiceModel.Activation.WebServiceHostFactory> in the .svc file associated with the service, as in the following example.</span></span>  
  
```  
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 <span data-ttu-id="2bd03-112">Alternativně můžete také použití konfigurace k přidání koncového bodu AJAX.</span><span class="sxs-lookup"><span data-stu-id="2bd03-112">Alternatively, you can also use configuration to add an AJAX endpoint.</span></span> <span data-ttu-id="2bd03-113">Použití <xref:System.ServiceModel.WebHttpBinding> na koncový bod služby a konfiguraci tohoto koncového bodu s <xref:System.ServiceModel.Description.WebHttpBehavior> jak je znázorněno v následujícím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="2bd03-113">Use the <xref:System.ServiceModel.WebHttpBinding> on the service endpoint and configure that endpoint with the <xref:System.ServiceModel.Description.WebHttpBehavior> as shown in the following code snippet.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="AjaxBehavior">  
          <webHttp/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Ajax.Samples.CityService">  
        <endpoint   
          address="ajaxEndpoint"  
          behaviorConfiguration="AjaxBehavior"  
          binding="webHttpBinding"  
          contract="Microsoft.Ajax.Samples.ICityService" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="2bd03-114">Funkční příklad najdete v článku [služba AJAX s JSON a XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="2bd03-114">For a working example, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>  
  
## <a name="creating-an-ajax-compatible-service-contract"></a><span data-ttu-id="2bd03-115">Vytváří se kontrakt služby kompatibilní s AJAX</span><span class="sxs-lookup"><span data-stu-id="2bd03-115">Creating an AJAX-Compatible Service Contract</span></span>  
 <span data-ttu-id="2bd03-116">Ve výchozím nastavení kontrakty služeb přístupná přes AJAX koncový bod vrácená data ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="2bd03-116">By default, service contracts exposed over an AJAX endpoint return data in the XML format.</span></span> <span data-ttu-id="2bd03-117">Ve výchozím nastavení je také přístupné prostřednictvím požadavků HTTP POST do adresy URL, které zahrnují adresu koncového bodu, za nímž následuje název operace, jak je znázorněno v následujícím příkladu operací služby.</span><span class="sxs-lookup"><span data-stu-id="2bd03-117">Also, by default service operations are accessible through HTTP POST requests to URLs that include the endpoint address followed by the operation name, as shown in the following example.</span></span>  
  
```  
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 <span data-ttu-id="2bd03-118">Tato operace je přístupný pomocí HTTP POST do `http://serviceaddress/endpointaddress/GetCities` a vrátí zprávu o XML.</span><span class="sxs-lookup"><span data-stu-id="2bd03-118">This operation is accessible using an HTTP POST to `http://serviceaddress/endpointaddress/GetCities` and return an XML message.</span></span>  
  
 <span data-ttu-id="2bd03-119">Celý Model programování webových můžete přizpůsobit tyto základní aspekty.</span><span class="sxs-lookup"><span data-stu-id="2bd03-119">You can use the full Web Programming Model to customize these basic aspects.</span></span> <span data-ttu-id="2bd03-120">Například můžete použít <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> atributy řídit příkaz HTTP, ke kterému odpovídá operaci nebo použít `UriTemplate` vlastnost těchto příslušných atributů k určení vlastní identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="2bd03-120">For example, you can use the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to control the HTTP verb to which the operation responds or use the `UriTemplate` property of these respective attributes to specify custom URIs.</span></span> <span data-ttu-id="2bd03-121">Další informace najdete v tématu [WCF Web HTTP programovací Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="2bd03-121">For more information, see the [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) topic.</span></span>  
  
 <span data-ttu-id="2bd03-122">Formát dat JSON se často používá služby AJAX.</span><span class="sxs-lookup"><span data-stu-id="2bd03-122">The JSON data format is often used in AJAX services.</span></span> <span data-ttu-id="2bd03-123">Pokud chcete vytvořit odpověď, která vrací JSON místo XML, nastavte <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (nebo <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) vlastnost <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="2bd03-123">To create an operation that returns JSON instead of XML, set the <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (or the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) property to <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="2bd03-124">[Serializace JSON samostatné](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) téma ukazuje, jak integrované .NET typy a data smlouvy typy mapy do formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="2bd03-124">The [Stand-Alone JSON Serialization](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) topic shows how built-in .NET types and data contract types map to JSON.</span></span>  
  
 <span data-ttu-id="2bd03-125">Za normálních okolností JSON požadavky a odpovědi obsahovat pouze jednu položku.</span><span class="sxs-lookup"><span data-stu-id="2bd03-125">Normally, JSON requests and responses consist of just one item.</span></span> <span data-ttu-id="2bd03-126">Pro předchozí `GetCities` operace, požadavek se podobá následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="2bd03-126">For the preceding `GetCities` operation, the request resembles the following statement.</span></span>  
  
```  
"na"  
```  
  
 <span data-ttu-id="2bd03-127">Odpověď na tento požadavek se podobá následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="2bd03-127">The response to that request resembles the following statement.</span></span>  
  
```  
["Nairobi", "Naples", "Nashville"]  
```  
  
 <span data-ttu-id="2bd03-128">Pokud operace trvá speciálním parametrem, musí být zabalené styl požadavek zabalit oba parametry v jednom objektu JSON.</span><span class="sxs-lookup"><span data-stu-id="2bd03-128">If the operation takes an extra parameter, the request style must be wrapped to wrap both parameters in a single JSON object.</span></span> <span data-ttu-id="2bd03-129">Příklad zprávy JSON tento styl je v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2bd03-129">An example of this style JSON message is in the following example.</span></span>  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 <span data-ttu-id="2bd03-130">Následující smlouvu přijme tuto zprávu.</span><span class="sxs-lookup"><span data-stu-id="2bd03-130">The following contract accepts this message.</span></span>  
  
```  
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a><span data-ttu-id="2bd03-131">Accessing AJAX Services</span><span class="sxs-lookup"><span data-stu-id="2bd03-131">Accessing AJAX Services</span></span>  
 <span data-ttu-id="2bd03-132">Koncových bodů WCF AJAX vždy přijímat žádosti JSON a XML.</span><span class="sxs-lookup"><span data-stu-id="2bd03-132">WCF AJAX endpoints always accept both JSON and XML requests.</span></span>  
  
 <span data-ttu-id="2bd03-133">Požadavky HTTP POST s obsahem typ "application/json" jsou považovány za JSON, a těmi, které mají typ obsahu, který označuje XML (například "text/xml") jsou považovány za XML.</span><span class="sxs-lookup"><span data-stu-id="2bd03-133">HTTP POST requests with a content-type of "application/json" are treated as JSON, and those with content-type that indicate XML (for example, "text/xml") are treated as XML.</span></span>  
  
 <span data-ttu-id="2bd03-134">Požadavky HTTP GET obsahovat všechny parametry požadavku v adrese URL samotného.</span><span class="sxs-lookup"><span data-stu-id="2bd03-134">HTTP GET requests contain all the request parameters in the URL itself.</span></span>  
  
 <span data-ttu-id="2bd03-135">Záleží uživateli rozhodnout, jak vytvořit požadavek protokolu HTTP na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="2bd03-135">It is up to the user to decide how to create the HTTP request to the endpoint.</span></span> <span data-ttu-id="2bd03-136">Kromě toho uživatel má plnou kontrolu nad ve formátu JSON, která tvoří text žádosti o sestavení.</span><span class="sxs-lookup"><span data-stu-id="2bd03-136">Also, the user has full control over constructing the JSON that forms the body of the request.</span></span> <span data-ttu-id="2bd03-137">Příklad vytvoření žádosti z jazyka JavaScript, najdete v článku [služba AJAX s JSON a XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="2bd03-137">For an example of creating a request from JavaScript, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>
