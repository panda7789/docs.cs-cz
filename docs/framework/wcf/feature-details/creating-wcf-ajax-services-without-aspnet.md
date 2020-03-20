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
# <a name="creating-wcf-ajax-services-without-aspnet"></a>Vytváření služeb WCF AJAX bez ASP.NET
Služby AJAX (Windows Communication Foundation) (WCF) jsou přístupné z libovolné webové stránky s podporou JavaScriptu, aniž by bylo nutné ASP.NET AJAX. Toto téma popisuje, jak vytvořit takovou službu WCF.  
  
 Pokyny k použití WCF s ASP.NET AJAX, naleznete [v tématu vytváření wcf služby pro ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).  
  
 Vytvoření služby WCF AJAX má tři části:  
  
- Vytvoření koncového bodu AJAX, který je přístupný z prohlížeče.  
  
- Vytvoření smlouvy o poskytování služeb kompatibilní s AJAX.  
  
- Přístup ke službám WCF AJAX.  
  
## <a name="creating-an-ajax-endpoint"></a>Vytvoření koncového bodu AJAX  
 Nejzákladnější způsob, jak povolit podporu AJAX ve <xref:System.ServiceModel.Activation.WebServiceHostFactory> službě WCF je použít v souboru .svc přidružené ke službě, jako v následujícím příkladu.  
  
```text
<%ServiceHost
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 Alternativně můžete také použít konfiguraci k přidání koncového bodu AJAX. <xref:System.ServiceModel.WebHttpBinding> Použijte koncový bod služby a nakonfigurujte tento koncový bod <xref:System.ServiceModel.Description.WebHttpBehavior> s, jak je znázorněno v následujícím fragmentu kódu.  
  
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
  
 Pracovní příklad naleznete v tématu [služba AJAX s JSON a XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="creating-an-ajax-compatible-service-contract"></a>Vytvoření smlouvy o poskytování služeb kompatibilní s AJAX  
 Ve výchozím nastavení vrátí smlouvy o službách vystavené přes koncový bod AJAX data ve formátu XML. Ve výchozím nastavení jsou také operace služby přístupné prostřednictvím požadavků HTTP POST adresám URL, které obsahují adresu koncového bodu následovanou názvem operace, jak je znázorněno v následujícím příkladu.  
  
```csharp
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 Tato operace je přístupná `http://serviceaddress/endpointaddress/GetCities` pomocí protokolu HTTP POST a vrátí zprávu XML.  
  
 Tyto základní aspekty můžete přizpůsobit pomocí úplného modelu webového programování. Můžete například použít <xref:System.ServiceModel.Web.WebGetAttribute> atributy nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> k řízení slovesa HTTP, na `UriTemplate` které operace reaguje, nebo použít vlastnost těchto příslušných atributů k určení vlastních identifikátorů URI. Další informace naleznete v tématu [WCF Web HTTP Programming Model.](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
  
 Datový formát JSON se často používá ve službách AJAX. Chcete-li vytvořit operaci, která vrátí položku <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> JSON místo <xref:System.ServiceModel.Web.WebMessageFormat.Json>jazyka XML, nastavte vlastnost (nebo ) na hodnotu <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>. Samostatné téma [serializace JSON](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) ukazuje, jak integrované typy rozhraní .NET a typy datových kontraktů jsou mapovány na JSON.  
  
 Za normálních okolností JSON požadavky a odpovědi se skládají pouze z jedné položky. Pro předchozí `GetCities` operaci požadavek se podobá následující příkaz.  
  
```json
"na"  
```  
  
 Odpověď na tento požadavek se podobá následující příkaz.  
  
```json
["Nairobi", "Naples", "Nashville"]  
```  
  
 Pokud operace trvá další parametr, styl požadavku musí být zabalen a zabalit oba parametry do jednoho objektu JSON. Příklad tohoto stylu zprávy JSON je v následujícím příkladu.  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 Následující smlouva přijímá tuto zprávu.  
  
```csharp
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a>Přístup ke službám AJAX  
 Koncové body WCF AJAX vždy přijímají požadavky JSON i XML.  
  
 Požadavky HTTP POST s typem obsahu "application/json" jsou považovány za JSON a požadavky s typem obsahu, které označují XML (například "text/xml"),jsou považovány za XML.  
  
 Požadavky HTTP GET obsahují všechny parametry požadavku v samotné adrese URL.  
  
 Je na uživateli, aby se rozhodl, jak vytvořit požadavek HTTP do koncového bodu. Také uživatel má plnou kontrolu nad konstrukci JSON, který tvoří tělo požadavku. Příklad vytvoření požadavku z JavaScriptu naleznete v části [Služba AJAX s JSON a XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).
