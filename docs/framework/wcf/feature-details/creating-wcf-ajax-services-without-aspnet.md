---
title: Vytváření služeb WCF AJAX bez ASP.NET
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b652bcd522a8eea81b3d1218fbd054ee0b2caea8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a><span data-ttu-id="ca130-102">Vytváření služeb WCF AJAX bez ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ca130-102">Creating WCF AJAX Services without ASP.NET</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="ca130-103"> Služby AJAX je přístupná z webové stránky povolen jazyk JavaScript, bez nutnosti prvku ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="ca130-103"> AJAX services can be accessed from any JavaScript-enabled Web page, without requiring ASP.NET AJAX.</span></span> <span data-ttu-id="ca130-104">Toto téma popisuje, jak vytvořit, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="ca130-104">This topic describes how to create such a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="ca130-105">Pokyny k používání [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pomocí prvku ASP.NET AJAX, najdete v části [vytváření služeb WCF pro ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span><span class="sxs-lookup"><span data-stu-id="ca130-105">For instructions on using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see [Creating WCF Services for ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span></span>  
  
 <span data-ttu-id="ca130-106">Existují tři části vytváření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba AJAX:</span><span class="sxs-lookup"><span data-stu-id="ca130-106">There are three parts to a creating a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX service:</span></span>  
  
-   <span data-ttu-id="ca130-107">Vytvoření AJAX koncový bod, který je přístupný z prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="ca130-107">Creating an AJAX endpoint that can be accessed from the browser.</span></span>  
  
-   <span data-ttu-id="ca130-108">Vytváření kontrakt služby AJAX kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="ca130-108">Creating an AJAX-compatible service contract.</span></span>  
  
-   <span data-ttu-id="ca130-109">Přístup ke službám WCF AJAX.</span><span class="sxs-lookup"><span data-stu-id="ca130-109">Accessing WCF AJAX services.</span></span>  
  
## <a name="creating-an-ajax-endpoint"></a><span data-ttu-id="ca130-110">Vytvoření koncového bodu AJAX</span><span class="sxs-lookup"><span data-stu-id="ca130-110">Creating an AJAX Endpoint</span></span>  
 <span data-ttu-id="ca130-111">Nejzákladnější způsob, jak povolit podporu jazyka AJAX [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby se má používat <xref:System.ServiceModel.Activation.WebServiceHostFactory> v souboru .svc přidružený k službě, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ca130-111">The most basic way to enable AJAX support in a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is to use the <xref:System.ServiceModel.Activation.WebServiceHostFactory> in the .svc file associated with the service, as in the following example.</span></span>  
  
```  
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 <span data-ttu-id="ca130-112">Alternativně můžete také použít konfigurace k přidání koncového bodu AJAX.</span><span class="sxs-lookup"><span data-stu-id="ca130-112">Alternatively, you can also use configuration to add an AJAX endpoint.</span></span> <span data-ttu-id="ca130-113">Použití <xref:System.ServiceModel.WebHttpBinding> na koncový bod služby a konfiguraci tohoto koncového bodu se <xref:System.ServiceModel.Description.WebHttpBehavior> jak je znázorněno v následující fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="ca130-113">Use the <xref:System.ServiceModel.WebHttpBinding> on the service endpoint and configure that endpoint with the <xref:System.ServiceModel.Description.WebHttpBehavior> as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="ca130-114">Příklad pracovní najdete v tématu [služba AJAX s protokoly JSON a XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ca130-114">For a working example, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>  
  
## <a name="creating-an-ajax-compatible-service-contract"></a><span data-ttu-id="ca130-115">Vytvoření kontrakt služby AJAX kompatibilní</span><span class="sxs-lookup"><span data-stu-id="ca130-115">Creating an AJAX-Compatible Service Contract</span></span>  
 <span data-ttu-id="ca130-116">Ve výchozím nastavení kontraktů služby zveřejňují přes AJAX koncový bod vracená data ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="ca130-116">By default, service contracts exposed over an AJAX endpoint return data in the XML format.</span></span> <span data-ttu-id="ca130-117">Ve výchozím nastavení jsou také přístupné prostřednictvím požadavky HTTP POST do adresy URL, které patří adresa koncového bodu, za nímž následuje název operace, jak je znázorněno v následujícím příkladu operací služby.</span><span class="sxs-lookup"><span data-stu-id="ca130-117">Also, by default service operations are accessible through HTTP POST requests to URLs that include the endpoint address followed by the operation name, as shown in the following example.</span></span>  
  
```  
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 <span data-ttu-id="ca130-118">Tato operace je přístupný pomocí HTTP POST do `http://serviceaddress/endpointaddress/GetCities` a vrátí zprávu XML.</span><span class="sxs-lookup"><span data-stu-id="ca130-118">This operation is accessible using an HTTP POST to `http://serviceaddress/endpointaddress/GetCities` and return an XML message.</span></span>  
  
 <span data-ttu-id="ca130-119">Úplný Model programování webových můžete přizpůsobit tyto základní aspekty.</span><span class="sxs-lookup"><span data-stu-id="ca130-119">You can use the full Web Programming Model to customize these basic aspects.</span></span> <span data-ttu-id="ca130-120">Například můžete použít <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> atributy řízení příkaz protokolu HTTP, na který odpoví operaci nebo použít `UriTemplate` vlastnost tyto příslušné atributy, které se mají zadat vlastní identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="ca130-120">For example, you can use the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to control the HTTP verb to which the operation responds or use the `UriTemplate` property of these respective attributes to specify custom URIs.</span></span> <span data-ttu-id="ca130-121">Další informace najdete v tématu [WCF Web HTTP programovací Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="ca130-121">For more information, see the [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) topic.</span></span>  
  
 <span data-ttu-id="ca130-122">Formát dat JSON se často používá v služby AJAX.</span><span class="sxs-lookup"><span data-stu-id="ca130-122">The JSON data format is often used in AJAX services.</span></span> <span data-ttu-id="ca130-123">Chcete-li vytvořit operace, která vrátí JSON místo XML, nastavte <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (nebo <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) vlastnost <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="ca130-123">To create an operation that returns JSON instead of XML, set the <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (or the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) property to <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="ca130-124">[Serializace JSON samostatné](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) téma ukazuje, jak předdefinované .NET typy a data kontrakt typy mapy do formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="ca130-124">The [Stand-Alone JSON Serialization](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) topic shows how built-in .NET types and data contract types map to JSON.</span></span>  
  
 <span data-ttu-id="ca130-125">Za normálních okolností JSON požadavky a odpovědi obsahovat pouze jednu položku.</span><span class="sxs-lookup"><span data-stu-id="ca130-125">Normally, JSON requests and responses consist of just one item.</span></span> <span data-ttu-id="ca130-126">Pro předchozí `GetCities` operace, požadavek se podobá následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="ca130-126">For the preceding `GetCities` operation, the request resembles the following statement.</span></span>  
  
```  
"na"  
```  
  
 <span data-ttu-id="ca130-127">Odpovědi na tento požadavek se podobá následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="ca130-127">The response to that request resembles the following statement.</span></span>  
  
```  
["Nairobi", "Naples", "Nashville"]  
```  
  
 <span data-ttu-id="ca130-128">Pokud operaci přijímá speciálním parametrem, musí být styl požadavek zabaleny zabalit oba parametry v jeden objekt JSON.</span><span class="sxs-lookup"><span data-stu-id="ca130-128">If the operation takes an extra parameter, the request style must be wrapped to wrap both parameters in a single JSON object.</span></span> <span data-ttu-id="ca130-129">Příklad této zprávy styl JSON je v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ca130-129">An example of this style JSON message is in the following example.</span></span>  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 <span data-ttu-id="ca130-130">Následující kontrakt přijme tuto zprávu.</span><span class="sxs-lookup"><span data-stu-id="ca130-130">The following contract accepts this message.</span></span>  
  
```  
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a><span data-ttu-id="ca130-131">Přístup ke službám AJAX</span><span class="sxs-lookup"><span data-stu-id="ca130-131">Accessing AJAX Services</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ca130-132"> Koncové body AJAX vždy příjem požadavků JSON a XML.</span><span class="sxs-lookup"><span data-stu-id="ca130-132"> AJAX endpoints always accept both JSON and XML requests.</span></span>  
  
 <span data-ttu-id="ca130-133">Požadavky HTTP POST s obsah typ "application/json" se považují za JSON a obsah typ, který označuje XML (například "text/xml") se považují za XML.</span><span class="sxs-lookup"><span data-stu-id="ca130-133">HTTP POST requests with a content-type of "application/json" are treated as JSON, and those with content-type that indicate XML (for example, "text/xml") are treated as XML.</span></span>  
  
 <span data-ttu-id="ca130-134">Požadavky HTTP GET obsahovat všechny parametry žádosti v adrese URL sám sebe.</span><span class="sxs-lookup"><span data-stu-id="ca130-134">HTTP GET requests contain all the request parameters in the URL itself.</span></span>  
  
 <span data-ttu-id="ca130-135">Je uživateli se rozhodnout, jak vytvořit požadavek HTTP ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="ca130-135">It is up to the user to decide how to create the HTTP request to the endpoint.</span></span> <span data-ttu-id="ca130-136">Také uživatel má plnou kontrolu nad vytváření JSON, která tvoří text žádosti.</span><span class="sxs-lookup"><span data-stu-id="ca130-136">Also, the user has full control over constructing the JSON that forms the body of the request.</span></span> <span data-ttu-id="ca130-137">Příklad vytvoření žádost z jazyka JavaScript, najdete v článku [služba AJAX s protokoly JSON a XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ca130-137">For an example of creating a request from JavaScript, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>
