---
title: Ukázka služby AJAX s protokoly JSON a XML
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: ca9bdbfa135ac7dc0b69589d4f8fce07bc4c4afe
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716218"
---
# <a name="ajax-service-with-json-and-xml-sample"></a>Ukázka služby AJAX s protokoly JSON a XML

Tento příklad ukazuje, jak použít Windows Communication Foundation (WCF) k vytvoření asynchronní služby JavaScriptu a XML (AJAX), která vrací buď JavaScript Object Notation (JSON) nebo XML data. Ke službě AJAX můžete přistupovat pomocí kódu jazyka JavaScript z klienta webového prohlížeče. Tato ukázka sestaví na [základní ukázce služby AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) .

Na rozdíl od ostatních ukázek AJAX Tato ukázka nepoužívá ASP.NET AJAX a ovládací prvek <xref:System.Web.UI.ScriptManager>. V případě některých dalších konfigurací je k dispozici služba WCF AJAX z jakékoli stránky HTML prostřednictvím JavaScriptu a tento scénář je zobrazen zde. Příklad použití WCF s ASP.NET AJAX naleznete v tématu [ukázky AJAX](ajax.md).

Tato ukázka ukazuje, jak přepnout typ odezvy operace mezi JSON a XML. Tato funkce je k dispozici bez ohledu na to, zda je služba nakonfigurována tak, aby k ní měl přístup ASP.NET AJAX nebo stránka klienta HTML/JavaScript.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

Chcete-li povolit použití klientů non-ASP.NET AJAX, použijte <xref:System.ServiceModel.Activation.WebServiceHostFactory> (není <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) v souboru. svc. <xref:System.ServiceModel.Activation.WebServiceHostFactory> přidá ke službě koncový bod <xref:System.ServiceModel.Description.WebHttpEndpoint> Standard. Koncový bod je nakonfigurovaný na prázdné adrese relativní vzhledem k souboru. svc; To znamená, že adresa služby je `http://localhost/ServiceModelSamples/service.svc`, bez dalších přípon, než je název operace.

`<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>`

Následující oddíl v souboru Web. config lze použít k provedení dalších změn konfigurace koncového bodu. Je možné ji odebrat, pokud nejsou potřeba žádné další změny.

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

Výchozí formát dat pro <xref:System.ServiceModel.Description.WebHttpEndpoint> je XML, zatímco výchozí formát dat pro <xref:System.ServiceModel.Description.WebScriptEndpoint> je JSON. Další informace najdete v tématu [vytváření služeb WCF AJAX bez ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).

Služba v následující ukázce je standardní služba WCF se dvěma operacemi. Obě operace vyžadují <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> styl těla u atributů <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute>, které jsou specifické pro `webHttp` chování a které nemají žádný vliv na přepínač formátu dat JSON nebo XML.

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathXml(double n1, double n2);
```

Formát odpovědi pro operaci je zadán jako XML, což je výchozí nastavení pro\<chování technologie [WebHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) . Je však vhodné explicitně zadat formát odpovědi.

Druhá operace používá atribut `WebInvokeAttribute` a explicitně určuje JSON místo XML pro odpověď.

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathJson(double n1, double n2);
```

Všimněte si, že v obou případech operace vrátí komplexní typ, `MathResult`, což je standardní typ kontraktu dat WCF.

Webová stránka klienta XmlAjaxClientPage. htm obsahuje kód JavaScriptu, který vyvolá jednu z předchozích dvou operací, když uživatel klikne na stránce **provést výpočet (návratový kód JSON)** nebo **provést výpočet (vrácení XML)** . Kód pro vyvolání služby vytvoří tělo JSON a odešle ho pomocí HTTP POST. Požadavek se v JavaScriptu vytvoří ručně, na rozdíl od ukázky [základní služby AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) a dalších ukázek pomocí ASP.NET AJAX.

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

Když služba odpoví, zobrazí se odpověď bez dalšího zpracování v textovém poli na stránce. To je implementováno pro demonstrační účely, které vám umožní přímo sledovat použité formáty dat XML a JSON.

```javascript
// Create result handler
xmlHttp.onreadystatechange=function(){
     if(xmlHttp.readyState == 4){
          document.getElementById("result").value = xmlHttp.responseText;
     }
}
```

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Sestavte řešení XmlAjaxService. sln, jak je popsáno v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Přejděte na `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (neotevírejte XmlAjaxClientPage. htm v prohlížeči z adresáře projektu).

## <a name="see-also"></a>Viz také:

- [Služba AJAX využívající HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
