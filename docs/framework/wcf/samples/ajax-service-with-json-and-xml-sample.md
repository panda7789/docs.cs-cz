---
title: Ukázka služby AJAX s protokoly JSON a XML
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: 1beb89c11fccefec24ccbebc3fe30033a646718d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520071"
---
# <a name="ajax-service-with-json-and-xml-sample"></a>Ukázka služby AJAX s protokoly JSON a XML
Tento příklad ukazuje, jak použít Windows Communication Foundation (WCF) k vytvoření služby asynchronní JavaScript a XML (AJAX), který vrací data JavaScript Object Notation (JSON) nebo XML. Služby AJAX můžete přistupovat pomocí kódu jazyka JavaScript z webového prohlížeče klienta. Tato ukázka je založena na [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) vzorku.  
  
 Na rozdíl od ostatních AJAX vzorků, tato ukázka nepoužívá technologie ASP.NET AJAX a <xref:System.Web.UI.ScriptManager> ovládacího prvku. Některé další konfigurace služeb WCF AJAX je přístupný z jakékoli stránky HTML pomocí JavaScriptu a tento scénář je znázorněna zde. Příklad použití WCF pomocí ASP.NET AJAX, naleznete v tématu [AJAX ukázky](https://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
 Tento příklad ukazuje, jak přepnout typ odpovědi z operace mezi JSON a XML. Tato funkce je dostupná bez ohledu na to, zda je služba nakonfigurována přistupovat pomocí technologie ASP.NET AJAX nebo stránku HTML/JavaScript klienta.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Chcete-li povolit používání technologie ASP.NET AJAX klientů, použijte <xref:System.ServiceModel.Activation.WebServiceHostFactory> (ne <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) v souboru SVC. <xref:System.ServiceModel.Activation.WebServiceHostFactory> Přidá <xref:System.ServiceModel.Description.WebHttpEndpoint> standardní koncový bod ke službě. Koncový bod je nakonfigurována na prázdnou adresu relativní k souboru .svc; To znamená, že je adresa služby http://localhost/ServiceModelSamples/service.svc, se žádné další přípony jiný než název operace.  
  
```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>  
```  
  
 Následující části v souboru Web.config je možné provést další změny konfigurace koncového bodu. Je možné odebrat, pokud nejsou potřeba žádné další změny.  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name="" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 Data výchozí formát pro <xref:System.ServiceModel.Description.WebHttpEndpoint> XML, se při výchozí formát dat pro <xref:System.ServiceModel.Description.WebScriptEndpoint> je JSON. Další informace najdete v tématu [vytváření služeb WCF AJAX bez ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).  
  
 Tato služba v následujícím příkladu je standardní služby WCF s dvě operace. Obě operace vyžadují <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> textu ve stylu <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> atributy, které jsou specifické pro `webHttp` chování a nemá žádný vliv na přepínač formátu dat JSON a XML.  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathXml(double n1, double n2);  
```

 Formát odpovědi pro operaci je zadán jako XML, což je výchozí nastavení [ \<webHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) chování. Ale je dobrým zvykem explicitně určit formát odpovědi.  
  
 Operace použije `WebInvokeAttribute` atribut a explicitně určí JSON místo XML pro odpověď.  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathJson(double n1, double n2);  
```

 Všimněte si, že v obou případech operace vrátí komplexní typ, `MathResult`, což je standardní typ kontraktu dat WCF.  
  
 Klient XmlAjaxClientPage.htm webová stránka obsahuje kód JavaScriptu, který vyvolá jednu z předchozí dvě operace, když uživatel klikne **provedení výpočtu (vrácený kód JSON)** nebo **provedení výpočtu (návratový XML)**  tlačítka na stránce. Kód se vyvolat službu vytvoří text JSON a odešle ji pomocí HTTP POST. Žádost je ručně vytvořené v jazyce JavaScript, na rozdíl od [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázky a další ukázky pomocí prvku ASP.NET AJAX.  

```csharp
// Create HTTP request  
var xmlHttp;  
// Request instantiation code omitted…  
// Result handler code omitted…  
  
// Build the operation URL  
var url = "service.svc/ajaxEndpoint/";  
url = url + operation;  
  
// Build the body of the JSON message  
var body = '{"n1":';  
body = body + document.getElementById("num1").value + ',"n2":';  
body = body + document.getElementById("num2").value + '}';  
  
// Send the HTTP request  
xmlHttp.open("POST", url, true);  
xmlHttp.setRequestHeader("Content-type", "application/json");  
xmlHttp.send(body);  
```

 Pokud služba odpoví, bez dalšího zpracování v textovém poli na stránce zobrazí odpověď. To je implementováno pro demonstrační účely můžete přímo sledovat formáty dat XML a JSON použít.  

```javascript
// Create result handler   
xmlHttp.onreadystatechange=function(){  
     if(xmlHttp.readyState == 4){  
          document.getElementById("result").value = xmlHttp.responseText;  
     }  
}  
```

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení XmlAjaxService.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Přejděte na http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm (neotevírejte XmlAjaxClientPage.htm v prohlížeči z adresáře projektu).  
  
## <a name="see-also"></a>Viz také  
 [Služba AJAX využívající HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
