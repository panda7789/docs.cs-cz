---
title: Vytváření služeb WCF AJAX bez ASP.NET
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: 04d2831407f4aa32c72aabbbff0e6fdde769bd23
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895086"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a><span data-ttu-id="9b30b-102">Vytváření služeb WCF AJAX bez ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9b30b-102">Creating WCF AJAX Services without ASP.NET</span></span>
<span data-ttu-id="9b30b-103">Služba Windows Communication Foundation (WCF) AJAX Services je dostupná z libovolné webové stránky s podporou JavaScriptu, aniž by to vyžadovalo ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="9b30b-103">Windows Communication Foundation (WCF) AJAX services can be accessed from any JavaScript-enabled Web page, without requiring ASP.NET AJAX.</span></span> <span data-ttu-id="9b30b-104">Toto téma popisuje, jak vytvořit takovou službu WCF.</span><span class="sxs-lookup"><span data-stu-id="9b30b-104">This topic describes how to create such a WCF service.</span></span>  
  
 <span data-ttu-id="9b30b-105">Pokyny k použití WCF s ASP.NET AJAX najdete v tématu [vytváření služeb WCF pro ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span><span class="sxs-lookup"><span data-stu-id="9b30b-105">For instructions on using WCF with ASP.NET AJAX, see [Creating WCF Services for ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span></span>  
  
 <span data-ttu-id="9b30b-106">Existují tři části pro vytvoření služby WCF AJAX:</span><span class="sxs-lookup"><span data-stu-id="9b30b-106">There are three parts to a creating a WCF AJAX service:</span></span>  
  
- <span data-ttu-id="9b30b-107">Vytvoření koncového bodu AJAX, který je přístupný z prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="9b30b-107">Creating an AJAX endpoint that can be accessed from the browser.</span></span>  
  
- <span data-ttu-id="9b30b-108">Vytvoření kontraktu služby kompatibilního s AJAX.</span><span class="sxs-lookup"><span data-stu-id="9b30b-108">Creating an AJAX-compatible service contract.</span></span>  
  
- <span data-ttu-id="9b30b-109">Přístup ke službám WCF AJAX.</span><span class="sxs-lookup"><span data-stu-id="9b30b-109">Accessing WCF AJAX services.</span></span>  
  
## <a name="creating-an-ajax-endpoint"></a><span data-ttu-id="9b30b-110">Vytvoření koncového bodu AJAX</span><span class="sxs-lookup"><span data-stu-id="9b30b-110">Creating an AJAX Endpoint</span></span>  
 <span data-ttu-id="9b30b-111">Nejzákladnější způsob, jak povolit podporu AJAX ve službě WCF, je použít <xref:System.ServiceModel.Activation.WebServiceHostFactory> v souboru. svc přidruženého ke službě, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9b30b-111">The most basic way to enable AJAX support in a WCF service is to use the <xref:System.ServiceModel.Activation.WebServiceHostFactory> in the .svc file associated with the service, as in the following example.</span></span>  
  
```text
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 <span data-ttu-id="9b30b-112">Alternativně můžete použít také konfiguraci pro přidání koncového bodu AJAX.</span><span class="sxs-lookup"><span data-stu-id="9b30b-112">Alternatively, you can also use configuration to add an AJAX endpoint.</span></span> <span data-ttu-id="9b30b-113">Použijte na koncovém bodu služby a nakonfigurujte tento koncový bod <xref:System.ServiceModel.Description.WebHttpBehavior> pomocí, jak je znázorněno v následujícím fragmentu kódu. <xref:System.ServiceModel.WebHttpBinding></span><span class="sxs-lookup"><span data-stu-id="9b30b-113">Use the <xref:System.ServiceModel.WebHttpBinding> on the service endpoint and configure that endpoint with the <xref:System.ServiceModel.Description.WebHttpBehavior> as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="9b30b-114">Pracovní příklad naleznete v tématu [Služba AJAX s JSON a XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="9b30b-114">For a working example, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>  
  
## <a name="creating-an-ajax-compatible-service-contract"></a><span data-ttu-id="9b30b-115">Vytvoření kontraktu služby kompatibilního s AJAX</span><span class="sxs-lookup"><span data-stu-id="9b30b-115">Creating an AJAX-Compatible Service Contract</span></span>  
 <span data-ttu-id="9b30b-116">Ve výchozím nastavení kontrakty služby vystavené přes koncový bod AJAX vrací data ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="9b30b-116">By default, service contracts exposed over an AJAX endpoint return data in the XML format.</span></span> <span data-ttu-id="9b30b-117">Ve výchozím nastavení jsou taky v rámci požadavků HTTP POST k adresám URL, které obsahují adresu koncového bodu následovaným názvem operace, dostupné tyto operace služby, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9b30b-117">Also, by default service operations are accessible through HTTP POST requests to URLs that include the endpoint address followed by the operation name, as shown in the following example.</span></span>  
  
```csharp
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 <span data-ttu-id="9b30b-118">Tato operace je přístupná pomocí HTTP Post `http://serviceaddress/endpointaddress/GetCities` a vrátí zprávu XML.</span><span class="sxs-lookup"><span data-stu-id="9b30b-118">This operation is accessible using an HTTP POST to `http://serviceaddress/endpointaddress/GetCities` and return an XML message.</span></span>  
  
 <span data-ttu-id="9b30b-119">K přizpůsobení těchto základních aspektů můžete použít úplný model webového programování.</span><span class="sxs-lookup"><span data-stu-id="9b30b-119">You can use the full Web Programming Model to customize these basic aspects.</span></span> <span data-ttu-id="9b30b-120">Můžete například použít <xref:System.ServiceModel.Web.WebGetAttribute> atributy nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> pro řízení příkazu http, na který `UriTemplate` operace reaguje, nebo použít vlastnost těchto odpovídajících atributů k určení vlastních identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="9b30b-120">For example, you can use the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to control the HTTP verb to which the operation responds or use the `UriTemplate` property of these respective attributes to specify custom URIs.</span></span> <span data-ttu-id="9b30b-121">Další informace naleznete v tématu [programovací model webového HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) .</span><span class="sxs-lookup"><span data-stu-id="9b30b-121">For more information, see the [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) topic.</span></span>  
  
 <span data-ttu-id="9b30b-122">Formát dat JSON se často používá ve službách AJAX.</span><span class="sxs-lookup"><span data-stu-id="9b30b-122">The JSON data format is often used in AJAX services.</span></span> <span data-ttu-id="9b30b-123">Chcete-li vytvořit operaci, která vrátí JSON namísto XML, nastavte <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> vlastnost ( <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>nebo) na <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="9b30b-123">To create an operation that returns JSON instead of XML, set the <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (or the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) property to <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="9b30b-124">V tématu [samostatné serializace JSON](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) se dozvíte, jak jsou integrované typy rozhraní .NET a typy kontraktů dat mapovány na JSON.</span><span class="sxs-lookup"><span data-stu-id="9b30b-124">The [Stand-Alone JSON Serialization](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) topic shows how built-in .NET types and data contract types map to JSON.</span></span>  
  
 <span data-ttu-id="9b30b-125">Žádosti a odpovědi JSON se obvykle skládají jenom z jedné položky.</span><span class="sxs-lookup"><span data-stu-id="9b30b-125">Normally, JSON requests and responses consist of just one item.</span></span> <span data-ttu-id="9b30b-126">U předchozí `GetCities` operace se požadavek podobá následujícímu příkazu.</span><span class="sxs-lookup"><span data-stu-id="9b30b-126">For the preceding `GetCities` operation, the request resembles the following statement.</span></span>  
  
```json
"na"  
```  
  
 <span data-ttu-id="9b30b-127">Odpověď na tento požadavek se podobá následujícímu příkazu.</span><span class="sxs-lookup"><span data-stu-id="9b30b-127">The response to that request resembles the following statement.</span></span>  
  
```json
["Nairobi", "Naples", "Nashville"]  
```  
  
 <span data-ttu-id="9b30b-128">Pokud operace převezme další parametr, musí být styl žádosti zabalený, aby bylo možné zabalit oba parametry v jednom objektu JSON.</span><span class="sxs-lookup"><span data-stu-id="9b30b-128">If the operation takes an extra parameter, the request style must be wrapped to wrap both parameters in a single JSON object.</span></span> <span data-ttu-id="9b30b-129">Příkladem zprávy JSON tohoto stylu je následující příklad.</span><span class="sxs-lookup"><span data-stu-id="9b30b-129">An example of this style JSON message is in the following example.</span></span>  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 <span data-ttu-id="9b30b-130">Tuto zprávu akceptuje následující smlouva.</span><span class="sxs-lookup"><span data-stu-id="9b30b-130">The following contract accepts this message.</span></span>  
  
```csharp
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a><span data-ttu-id="9b30b-131">Přístup ke službám AJAX</span><span class="sxs-lookup"><span data-stu-id="9b30b-131">Accessing AJAX Services</span></span>  
 <span data-ttu-id="9b30b-132">Koncové body WCF AJAX vždy přijímají obě požadavky JSON i XML.</span><span class="sxs-lookup"><span data-stu-id="9b30b-132">WCF AJAX endpoints always accept both JSON and XML requests.</span></span>  
  
 <span data-ttu-id="9b30b-133">Požadavky HTTP POST s typem obsahu "Application/JSON" se považují za JSON a ty s typem obsahu, které označují XML (například "text/XML"), se považují za XML.</span><span class="sxs-lookup"><span data-stu-id="9b30b-133">HTTP POST requests with a content-type of "application/json" are treated as JSON, and those with content-type that indicate XML (for example, "text/xml") are treated as XML.</span></span>  
  
 <span data-ttu-id="9b30b-134">Požadavky HTTP GET obsahují všechny parametry žádosti v samotné adrese URL.</span><span class="sxs-lookup"><span data-stu-id="9b30b-134">HTTP GET requests contain all the request parameters in the URL itself.</span></span>  
  
 <span data-ttu-id="9b30b-135">Uživatel se rozhodne, jak vytvořit požadavek HTTP na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="9b30b-135">It is up to the user to decide how to create the HTTP request to the endpoint.</span></span> <span data-ttu-id="9b30b-136">Uživatel má také úplnou kontrolu nad vytvářením JSON, která tvoří tělo žádosti.</span><span class="sxs-lookup"><span data-stu-id="9b30b-136">Also, the user has full control over constructing the JSON that forms the body of the request.</span></span> <span data-ttu-id="9b30b-137">Příklad vytvoření požadavku z JavaScriptu naleznete v tématu [Služba AJAX s JSON a XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="9b30b-137">For an example of creating a request from JavaScript, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>
