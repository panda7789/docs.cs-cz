---
title: Vytváření služeb WCF AJAX bez ASP.NET
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: f4d1d093132c501844aacbaa9cf28ecc3cede442
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185240"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a><span data-ttu-id="79075-102">Vytváření služeb WCF AJAX bez ASP.NET</span><span class="sxs-lookup"><span data-stu-id="79075-102">Creating WCF AJAX Services without ASP.NET</span></span>
<span data-ttu-id="79075-103">Služby AJAX (Windows Communication Foundation) (WCF) jsou přístupné z libovolné webové stránky s podporou JavaScriptu, aniž by bylo nutné ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="79075-103">Windows Communication Foundation (WCF) AJAX services can be accessed from any JavaScript-enabled Web page, without requiring ASP.NET AJAX.</span></span> <span data-ttu-id="79075-104">Toto téma popisuje, jak vytvořit takovou službu WCF.</span><span class="sxs-lookup"><span data-stu-id="79075-104">This topic describes how to create such a WCF service.</span></span>  
  
 <span data-ttu-id="79075-105">Pokyny k použití WCF s ASP.NET AJAX, naleznete [v tématu vytváření wcf služby pro ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span><span class="sxs-lookup"><span data-stu-id="79075-105">For instructions on using WCF with ASP.NET AJAX, see [Creating WCF Services for ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span></span>  
  
 <span data-ttu-id="79075-106">Vytvoření služby WCF AJAX má tři části:</span><span class="sxs-lookup"><span data-stu-id="79075-106">There are three parts to a creating a WCF AJAX service:</span></span>  
  
- <span data-ttu-id="79075-107">Vytvoření koncového bodu AJAX, který je přístupný z prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="79075-107">Creating an AJAX endpoint that can be accessed from the browser.</span></span>  
  
- <span data-ttu-id="79075-108">Vytvoření smlouvy o poskytování služeb kompatibilní s AJAX.</span><span class="sxs-lookup"><span data-stu-id="79075-108">Creating an AJAX-compatible service contract.</span></span>  
  
- <span data-ttu-id="79075-109">Přístup ke službám WCF AJAX.</span><span class="sxs-lookup"><span data-stu-id="79075-109">Accessing WCF AJAX services.</span></span>  
  
## <a name="creating-an-ajax-endpoint"></a><span data-ttu-id="79075-110">Vytvoření koncového bodu AJAX</span><span class="sxs-lookup"><span data-stu-id="79075-110">Creating an AJAX Endpoint</span></span>  
 <span data-ttu-id="79075-111">Nejzákladnější způsob, jak povolit podporu AJAX ve <xref:System.ServiceModel.Activation.WebServiceHostFactory> službě WCF je použít v souboru .svc přidružené ke službě, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="79075-111">The most basic way to enable AJAX support in a WCF service is to use the <xref:System.ServiceModel.Activation.WebServiceHostFactory> in the .svc file associated with the service, as in the following example.</span></span>  
  
```text
<%ServiceHost
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 <span data-ttu-id="79075-112">Alternativně můžete také použít konfiguraci k přidání koncového bodu AJAX.</span><span class="sxs-lookup"><span data-stu-id="79075-112">Alternatively, you can also use configuration to add an AJAX endpoint.</span></span> <span data-ttu-id="79075-113"><xref:System.ServiceModel.WebHttpBinding> Použijte koncový bod služby a nakonfigurujte tento koncový bod <xref:System.ServiceModel.Description.WebHttpBehavior> s, jak je znázorněno v následujícím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="79075-113">Use the <xref:System.ServiceModel.WebHttpBinding> on the service endpoint and configure that endpoint with the <xref:System.ServiceModel.Description.WebHttpBehavior> as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="79075-114">Pracovní příklad naleznete v tématu [služba AJAX s JSON a XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="79075-114">For a working example, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>  
  
## <a name="creating-an-ajax-compatible-service-contract"></a><span data-ttu-id="79075-115">Vytvoření smlouvy o poskytování služeb kompatibilní s AJAX</span><span class="sxs-lookup"><span data-stu-id="79075-115">Creating an AJAX-Compatible Service Contract</span></span>  
 <span data-ttu-id="79075-116">Ve výchozím nastavení vrátí smlouvy o službách vystavené přes koncový bod AJAX data ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="79075-116">By default, service contracts exposed over an AJAX endpoint return data in the XML format.</span></span> <span data-ttu-id="79075-117">Ve výchozím nastavení jsou také operace služby přístupné prostřednictvím požadavků HTTP POST adresám URL, které obsahují adresu koncového bodu následovanou názvem operace, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="79075-117">Also, by default service operations are accessible through HTTP POST requests to URLs that include the endpoint address followed by the operation name, as shown in the following example.</span></span>  
  
```csharp
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 <span data-ttu-id="79075-118">Tato operace je přístupná `http://serviceaddress/endpointaddress/GetCities` pomocí protokolu HTTP POST a vrátí zprávu XML.</span><span class="sxs-lookup"><span data-stu-id="79075-118">This operation is accessible using an HTTP POST to `http://serviceaddress/endpointaddress/GetCities` and return an XML message.</span></span>  
  
 <span data-ttu-id="79075-119">Tyto základní aspekty můžete přizpůsobit pomocí úplného modelu webového programování.</span><span class="sxs-lookup"><span data-stu-id="79075-119">You can use the full Web Programming Model to customize these basic aspects.</span></span> <span data-ttu-id="79075-120">Můžete například použít <xref:System.ServiceModel.Web.WebGetAttribute> atributy nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> k řízení slovesa HTTP, na `UriTemplate` které operace reaguje, nebo použít vlastnost těchto příslušných atributů k určení vlastních identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="79075-120">For example, you can use the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to control the HTTP verb to which the operation responds or use the `UriTemplate` property of these respective attributes to specify custom URIs.</span></span> <span data-ttu-id="79075-121">Další informace naleznete v tématu [WCF Web HTTP Programming Model.](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)</span><span class="sxs-lookup"><span data-stu-id="79075-121">For more information, see the [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) topic.</span></span>  
  
 <span data-ttu-id="79075-122">Datový formát JSON se často používá ve službách AJAX.</span><span class="sxs-lookup"><span data-stu-id="79075-122">The JSON data format is often used in AJAX services.</span></span> <span data-ttu-id="79075-123">Chcete-li vytvořit operaci, která vrátí položku <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> JSON místo <xref:System.ServiceModel.Web.WebMessageFormat.Json>jazyka XML, nastavte vlastnost (nebo ) na hodnotu <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>.</span><span class="sxs-lookup"><span data-stu-id="79075-123">To create an operation that returns JSON instead of XML, set the <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (or the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) property to <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="79075-124">Samostatné téma [serializace JSON](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) ukazuje, jak integrované typy rozhraní .NET a typy datových kontraktů jsou mapovány na JSON.</span><span class="sxs-lookup"><span data-stu-id="79075-124">The [Stand-Alone JSON Serialization](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) topic shows how built-in .NET types and data contract types map to JSON.</span></span>  
  
 <span data-ttu-id="79075-125">Za normálních okolností JSON požadavky a odpovědi se skládají pouze z jedné položky.</span><span class="sxs-lookup"><span data-stu-id="79075-125">Normally, JSON requests and responses consist of just one item.</span></span> <span data-ttu-id="79075-126">Pro předchozí `GetCities` operaci požadavek se podobá následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="79075-126">For the preceding `GetCities` operation, the request resembles the following statement.</span></span>  
  
```json
"na"  
```  
  
 <span data-ttu-id="79075-127">Odpověď na tento požadavek se podobá následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="79075-127">The response to that request resembles the following statement.</span></span>  
  
```json
["Nairobi", "Naples", "Nashville"]  
```  
  
 <span data-ttu-id="79075-128">Pokud operace trvá další parametr, styl požadavku musí být zabalen a zabalit oba parametry do jednoho objektu JSON.</span><span class="sxs-lookup"><span data-stu-id="79075-128">If the operation takes an extra parameter, the request style must be wrapped to wrap both parameters in a single JSON object.</span></span> <span data-ttu-id="79075-129">Příklad tohoto stylu zprávy JSON je v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="79075-129">An example of this style JSON message is in the following example.</span></span>  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 <span data-ttu-id="79075-130">Následující smlouva přijímá tuto zprávu.</span><span class="sxs-lookup"><span data-stu-id="79075-130">The following contract accepts this message.</span></span>  
  
```csharp
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a><span data-ttu-id="79075-131">Přístup ke službám AJAX</span><span class="sxs-lookup"><span data-stu-id="79075-131">Accessing AJAX Services</span></span>  
 <span data-ttu-id="79075-132">Koncové body WCF AJAX vždy přijímají požadavky JSON i XML.</span><span class="sxs-lookup"><span data-stu-id="79075-132">WCF AJAX endpoints always accept both JSON and XML requests.</span></span>  
  
 <span data-ttu-id="79075-133">Požadavky HTTP POST s typem obsahu "application/json" jsou považovány za JSON a požadavky s typem obsahu, které označují XML (například "text/xml"),jsou považovány za XML.</span><span class="sxs-lookup"><span data-stu-id="79075-133">HTTP POST requests with a content-type of "application/json" are treated as JSON, and those with content-type that indicate XML (for example, "text/xml") are treated as XML.</span></span>  
  
 <span data-ttu-id="79075-134">Požadavky HTTP GET obsahují všechny parametry požadavku v samotné adrese URL.</span><span class="sxs-lookup"><span data-stu-id="79075-134">HTTP GET requests contain all the request parameters in the URL itself.</span></span>  
  
 <span data-ttu-id="79075-135">Je na uživateli, aby se rozhodl, jak vytvořit požadavek HTTP do koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="79075-135">It is up to the user to decide how to create the HTTP request to the endpoint.</span></span> <span data-ttu-id="79075-136">Také uživatel má plnou kontrolu nad konstrukci JSON, který tvoří tělo požadavku.</span><span class="sxs-lookup"><span data-stu-id="79075-136">Also, the user has full control over constructing the JSON that forms the body of the request.</span></span> <span data-ttu-id="79075-137">Příklad vytvoření požadavku z JavaScriptu naleznete v části [Služba AJAX s JSON a XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="79075-137">For an example of creating a request from JavaScript, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>
