---
title: Ukázka služby AJAX s protokoly JSON a XML
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: 32964c287b0064daf529aa4c1e28f0927d29a6d5
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807342"
---
# <a name="ajax-service-with-json-and-xml-sample"></a>Ukázka služby AJAX s protokoly JSON a XML
Tento příklad znázorňuje, jak používat Windows Communication Foundation (WCF) k vytvoření služby asynchronní JavaScript a XML (AJAX), který vrací data JavaScript Object Notation (JSON) nebo XML. Služby AJAX můžete přistupovat pomocí kódu jazyka JavaScript z webového prohlížeče klienta. Tato ukázka je založena na [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázka.  
  
 Na rozdíl od jiných AJAX ukázky, tato ukázka nepoužívá prvku ASP.NET AJAX a <xref:System.Web.UI.ScriptManager> ovládacího prvku. S určitou další konfiguraci služby WCF AJAX lze přistupovat z libovolné stránce HTML pomocí jazyka JavaScript a tento scénář je zobrazen v tomto poli. Příklad WCF pomocí prvku ASP.NET AJAX, naleznete v části [AJAX ukázky](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
 Tento příklad ukazuje, jak přepínat typ odpovědi operace mezi JSON a XML. Tato funkce je k dispozici bez ohledu na to, zda je služba nakonfigurována pro přistupovat pomocí prvku ASP.NET AJAX nebo stránku HTML/JavaScript klienta.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Pokud chcete povolit použití ASP.NET AJAX klientů, použijte <xref:System.ServiceModel.Activation.WebServiceHostFactory> (ne <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) v souboru .svc. <xref:System.ServiceModel.Activation.WebServiceHostFactory> Přidá <xref:System.ServiceModel.Description.WebHttpEndpoint> standardní koncového bodu služby. Koncový bod je konfigurována na prázdnou adresu relativně k souboru .svc; To znamená, že adresa služby je http://localhost/ServiceModelSamples/service.svc, s žádné další přípony jiný než název operace.  
  
```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>  
```  
  
 V následující části v souboru Web.config lze provést další změny konfigurace ke koncovému bodu. Může být odebrán, pokud jsou potřeba žádné další změny.  
  
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
  
 Výchozí data formátu pro <xref:System.ServiceModel.Description.WebHttpEndpoint> XML, je při výchozí formát dat pro <xref:System.ServiceModel.Description.WebScriptEndpoint> je JSON. Další informace najdete v tématu [vytváření služeb WCF AJAX bez ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).  
  
 Služba v následující ukázce je standardní služby WCF s dvěma operacemi. Obě operace vyžadují <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> body styl na <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> atributy, které je specifická pro `webHttp` chování a nemá žádný vliv na přepínač formátu dat JSON/XML.  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathXml(double n1, double n2);  
```

 Formát odpovědi pro tuto operaci je zadán jako XML, který je výchozí nastavení [ \<webHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) chování. Ale je dobrým zvykem explicitně zadat formát odpovědi.  
  
 Používá jiné operace `WebInvokeAttribute` atribut a explicitně určuje JSON místo XML pro odpověď.  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathJson(double n1, double n2);  
```

 Všimněte si, že v obou případech vrátí operace komplexního typu, `MathResult`, což je standardní typ kontraktu dat WCF.  
  
 Klient XmlAjaxClientPage.htm webová stránka obsahuje kód JavaScript, který některé z předchozích dvou operací vyvolá, když uživatel klikne **provádění výpočtu (návratový JSON)** nebo **provádění výpočtu (návratový XML)**  tlačítka na stránce. Kód k vyvolání služby vytvoří text JSON a odešle ji pomocí HTTP POST. Požadavek je vytvořen ručně v jazyce JavaScript, na rozdíl od [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázka a další ukázky pomocí prvku ASP.NET AJAX.  

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

 Když službu odpoví, zobrazí se bez dalšího zpracování do textového pole na stránce odpovědi. Tato možnost je implementovaná pro demonstrační účely, abyste mohli přímo sledovat XML a JSON formáty dat použít.  

```javascript
// Create result handler   
xmlHttp.onreadystatechange=function(){  
     if(xmlHttp.readyState == 4){  
          document.getElementById("result").value = xmlHttp.responseText;  
     }  
}  
```

> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení XmlAjaxService.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Přejděte na http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm (neotevírejte XmlAjaxClientPage.htm v prohlížeči z adresáře projektu).  
  
## <a name="see-also"></a>Viz také  
 [Služba AJAX využívající HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
