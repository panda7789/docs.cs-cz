---
title: Vytváření služeb WCF AJAX bez ASP.NET
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: b5f0f730f90227dcccc7e5ebf533d80a28f6e6eb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599292"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a>Vytváření služeb WCF AJAX bez ASP.NET
Služba Windows Communication Foundation (WCF) AJAX Services je dostupná z libovolné webové stránky s podporou JavaScriptu, aniž by to vyžadovalo ASP.NET AJAX. Toto téma popisuje, jak vytvořit takovou službu WCF.  
  
 Pokyny k použití WCF s ASP.NET AJAX najdete v tématu [vytváření služeb WCF pro ASP.NET AJAX](creating-wcf-services-for-aspnet-ajax.md).  
  
 Existují tři části pro vytvoření služby WCF AJAX:  
  
- Vytvoření koncového bodu AJAX, který je přístupný z prohlížeče.  
  
- Vytvoření kontraktu služby kompatibilního s AJAX.  
  
- Přístup ke službám WCF AJAX.  
  
## <a name="creating-an-ajax-endpoint"></a>Vytvoření koncového bodu AJAX  
 Nejzákladnější způsob, jak povolit podporu AJAX ve službě WCF, je použít <xref:System.ServiceModel.Activation.WebServiceHostFactory> v souboru. svc přidruženého ke službě, jak je uvedeno v následujícím příkladu.  
  
```text
<%ServiceHost
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 Alternativně můžete použít také konfiguraci pro přidání koncového bodu AJAX. Použijte na <xref:System.ServiceModel.WebHttpBinding> koncovém bodu služby a nakonfigurujte tento koncový bod pomocí, <xref:System.ServiceModel.Description.WebHttpBehavior> jak je znázorněno v následujícím fragmentu kódu.  
  
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
  
 Pracovní příklad naleznete v tématu [Služba AJAX s JSON a XML](../samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="creating-an-ajax-compatible-service-contract"></a>Vytvoření kontraktu služby kompatibilního s AJAX  
 Ve výchozím nastavení kontrakty služby vystavené přes koncový bod AJAX vrací data ve formátu XML. Ve výchozím nastavení jsou taky v rámci požadavků HTTP POST k adresám URL, které obsahují adresu koncového bodu následovaným názvem operace, dostupné tyto operace služby, jak je znázorněno v následujícím příkladu.  
  
```csharp
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 Tato operace je přístupná pomocí HTTP POST `http://serviceaddress/endpointaddress/GetCities` a vrátí zprávu XML.  
  
 K přizpůsobení těchto základních aspektů můžete použít úplný model webového programování. Můžete například použít <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> atributy nebo pro řízení příkazu http, na který operace reaguje, nebo použít `UriTemplate` vlastnost těchto odpovídajících atributů k určení vlastních identifikátorů URI. Další informace naleznete v tématu [programovací model webového HTTP WCF](wcf-web-http-programming-model.md) .  
  
 Formát dat JSON se často používá ve službách AJAX. Chcete-li vytvořit operaci, která vrátí JSON namísto XML, nastavte <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> vlastnost (nebo <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> ) na <xref:System.ServiceModel.Web.WebMessageFormat.Json> . V tématu [samostatné serializace JSON](stand-alone-json-serialization.md) se dozvíte, jak jsou integrované typy rozhraní .NET a typy kontraktů dat mapovány na JSON.  
  
 Žádosti a odpovědi JSON se obvykle skládají jenom z jedné položky. U předchozí `GetCities` operace se požadavek podobá následujícímu příkazu.  
  
```json
"na"  
```  
  
 Odpověď na tento požadavek se podobá následujícímu příkazu.  
  
```json
["Nairobi", "Naples", "Nashville"]  
```  
  
 Pokud operace převezme další parametr, musí být styl žádosti zabalený, aby bylo možné zabalit oba parametry v jednom objektu JSON. Příkladem zprávy JSON tohoto stylu je následující příklad.  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 Tuto zprávu akceptuje následující smlouva.  
  
```csharp
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a>Přístup ke službám AJAX  
 Koncové body WCF AJAX vždy přijímají obě požadavky JSON i XML.  
  
 Požadavky HTTP POST s typem obsahu "Application/JSON" se považují za JSON a ty s typem obsahu, které označují XML (například "text/XML"), se považují za XML.  
  
 Požadavky HTTP GET obsahují všechny parametry žádosti v samotné adrese URL.  
  
 Uživatel se rozhodne, jak vytvořit požadavek HTTP na koncový bod. Uživatel má také úplnou kontrolu nad vytvářením JSON, která tvoří tělo žádosti. Příklad vytvoření požadavku z JavaScriptu naleznete v tématu [Služba AJAX s JSON a XML](../samples/ajax-service-with-json-and-xml-sample.md).
