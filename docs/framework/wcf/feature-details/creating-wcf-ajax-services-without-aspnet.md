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
# <a name="creating-wcf-ajax-services-without-aspnet"></a>Vytváření služeb WCF AJAX bez ASP.NET
AJAX služba Windows Communication Foundation (WCF) je přístupný z jakékoli stránky webové povolen jazyk JavaScript bez nutnosti technologie ASP.NET AJAX. Toto téma popisuje postup vytvoření služby WCF.  
  
 Pokyny týkající se použití WCF pomocí ASP.NET AJAX, naleznete v tématu [vytváření služeb WCF pro ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).  
  
 Existují tři části vytváření služeb WCF AJAX:  
  
- Vytvoření koncového bodu AJAX, který je přístupný z prohlížeče.  
  
- Vytváří se kontrakt služby kompatibilní s AJAX.  
  
- Přístup ke službám WCF AJAX.  
  
## <a name="creating-an-ajax-endpoint"></a>Vytváří se koncový bod AJAX  
 Základní způsob, jak povolit podporu AJAX služba WCF je použít <xref:System.ServiceModel.Activation.WebServiceHostFactory> v souboru SVC přidružená ke službě, jako v následujícím příkladu.  
  
```  
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 Alternativně můžete také použití konfigurace k přidání koncového bodu AJAX. Použití <xref:System.ServiceModel.WebHttpBinding> na koncový bod služby a konfiguraci tohoto koncového bodu s <xref:System.ServiceModel.Description.WebHttpBehavior> jak je znázorněno v následujícím fragmentu kódu.  
  
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
  
 Funkční příklad najdete v článku [služba AJAX s JSON a XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="creating-an-ajax-compatible-service-contract"></a>Vytváří se kontrakt služby kompatibilní s AJAX  
 Ve výchozím nastavení kontrakty služeb přístupná přes AJAX koncový bod vrácená data ve formátu XML. Ve výchozím nastavení je také přístupné prostřednictvím požadavků HTTP POST do adresy URL, které zahrnují adresu koncového bodu, za nímž následuje název operace, jak je znázorněno v následujícím příkladu operací služby.  
  
```  
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 Tato operace je přístupný pomocí HTTP POST do `http://serviceaddress/endpointaddress/GetCities` a vrátí zprávu o XML.  
  
 Celý Model programování webových můžete přizpůsobit tyto základní aspekty. Například můžete použít <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> atributy řídit příkaz HTTP, ke kterému odpovídá operaci nebo použít `UriTemplate` vlastnost těchto příslušných atributů k určení vlastní identifikátory URI. Další informace najdete v tématu [WCF Web HTTP programovací Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) tématu.  
  
 Formát dat JSON se často používá služby AJAX. Pokud chcete vytvořit odpověď, která vrací JSON místo XML, nastavte <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (nebo <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) vlastnost <xref:System.ServiceModel.Web.WebMessageFormat.Json>. [Serializace JSON samostatné](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) téma ukazuje, jak integrované .NET typy a data smlouvy typy mapy do formátu JSON.  
  
 Za normálních okolností JSON požadavky a odpovědi obsahovat pouze jednu položku. Pro předchozí `GetCities` operace, požadavek se podobá následující příkaz.  
  
```  
"na"  
```  
  
 Odpověď na tento požadavek se podobá následující příkaz.  
  
```  
["Nairobi", "Naples", "Nashville"]  
```  
  
 Pokud operace trvá speciálním parametrem, musí být zabalené styl požadavek zabalit oba parametry v jednom objektu JSON. Příklad zprávy JSON tento styl je v následujícím příkladu.  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 Následující smlouvu přijme tuto zprávu.  
  
```  
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a>Accessing AJAX Services  
 Koncových bodů WCF AJAX vždy přijímat žádosti JSON a XML.  
  
 Požadavky HTTP POST s obsahem typ "application/json" jsou považovány za JSON, a těmi, které mají typ obsahu, který označuje XML (například "text/xml") jsou považovány za XML.  
  
 Požadavky HTTP GET obsahovat všechny parametry požadavku v adrese URL samotného.  
  
 Záleží uživateli rozhodnout, jak vytvořit požadavek protokolu HTTP na koncový bod. Kromě toho uživatel má plnou kontrolu nad ve formátu JSON, která tvoří text žádosti o sestavení. Příklad vytvoření žádosti z jazyka JavaScript, najdete v článku [služba AJAX s JSON a XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).
