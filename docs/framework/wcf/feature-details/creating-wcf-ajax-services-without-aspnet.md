---
title: "Vytváření služeb WCF AJAX bez ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 70926e1deb9b4911a7d89d49280b9a0e6068cc42
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a>Vytváření služeb WCF AJAX bez ASP.NET
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Služby AJAX je přístupná z webové stránky povolen jazyk JavaScript, bez nutnosti prvku ASP.NET AJAX. Toto téma popisuje, jak vytvořit, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.  
  
 Pokyny k používání [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pomocí prvku ASP.NET AJAX, najdete v části [vytváření služeb WCF pro ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).  
  
 Existují tři části vytváření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba AJAX:  
  
-   Vytvoření AJAX koncový bod, který je přístupný z prohlížeče.  
  
-   Vytváření kontrakt služby AJAX kompatibilní.  
  
-   Přístup ke službám WCF AJAX.  
  
## <a name="creating-an-ajax-endpoint"></a>Vytvoření koncového bodu AJAX  
 Nejzákladnější způsob, jak povolit podporu jazyka AJAX [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby se má používat <xref:System.ServiceModel.Activation.WebServiceHostFactory> v souboru .svc přidružený k službě, jako v následujícím příkladu.  
  
```  
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 Alternativně můžete také použít konfigurace k přidání koncového bodu AJAX. Použití <xref:System.ServiceModel.WebHttpBinding> na koncový bod služby a konfiguraci tohoto koncového bodu se <xref:System.ServiceModel.Description.WebHttpBehavior> jak je znázorněno v následující fragment kódu.  
  
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
  
 Příklad pracovní najdete v tématu [služba AJAX s protokoly JSON a XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="creating-an-ajax-compatible-service-contract"></a>Vytvoření kontrakt služby AJAX kompatibilní  
 Ve výchozím nastavení kontraktů služby zveřejňují přes AJAX koncový bod vracená data ve formátu XML. Ve výchozím nastavení jsou také přístupné prostřednictvím požadavky HTTP POST do adresy URL, které patří adresa koncového bodu, za nímž následuje název operace, jak je znázorněno v následujícím příkladu operací služby.  
  
```  
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 Tato operace je přístupný pomocí HTTP POST do `http://serviceaddress/endpointaddress/GetCities` a vrátí zprávu XML.  
  
 Úplný Model programování webových můžete přizpůsobit tyto základní aspekty. Například můžete použít <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> atributy řízení příkaz protokolu HTTP, na který odpoví operaci nebo použít `UriTemplate` vlastnost tyto příslušné atributy, které se mají zadat vlastní identifikátory URI. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][WCF Web HTTP programovací Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) tématu.  
  
 Formát dat JSON se často používá v služby AJAX. Chcete-li vytvořit operace, která vrátí JSON místo XML, nastavte <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (nebo <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) vlastnost <xref:System.ServiceModel.Web.WebMessageFormat.Json>. [Serializace JSON samostatné](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) téma ukazuje, jak předdefinované .NET typy a data kontrakt typy mapy do formátu JSON.  
  
 Za normálních okolností JSON požadavky a odpovědi obsahovat pouze jednu položku. Pro předchozí `GetCities` operace, požadavek se podobá následující příkaz.  
  
```  
"na"  
```  
  
 Odpovědi na tento požadavek se podobá následující příkaz.  
  
```  
["Nairobi", "Naples", "Nashville"]  
```  
  
 Pokud operaci přijímá speciálním parametrem, musí být styl požadavek zabaleny zabalit oba parametry v jeden objekt JSON. Příklad této zprávy styl JSON je v následujícím příkladu.  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 Následující kontrakt přijme tuto zprávu.  
  
```  
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a>Přístup ke službám AJAX  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Koncové body AJAX vždy příjem požadavků JSON a XML.  
  
 Požadavky HTTP POST s obsah typ "application/json" se považují za JSON a obsah typ, který označuje XML (například "text/xml") se považují za XML.  
  
 Požadavky HTTP GET obsahovat všechny parametry žádosti v adrese URL sám sebe.  
  
 Je uživateli se rozhodnout, jak vytvořit požadavek HTTP ke koncovému bodu. Také uživatel má plnou kontrolu nad vytváření JSON, která tvoří text žádosti. Příklad vytvoření žádost z jazyka JavaScript, najdete v článku [služba AJAX s protokoly JSON a XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).
