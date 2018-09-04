---
title: Základní služba AJAX
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: d8da6469101511b6b5a9ce19a11f1e5e3fe9d83e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524880"
---
# <a name="basic-ajax-service"></a>Základní služba AJAX
Tento příklad ukazuje, jak pomocí služby Windows Communication Foundation (WCF) základní asynchronní jazyka JavaScript technologie ASP.NET a XML (AJAX) službu (služba, která můžete přistupovat pomocí kódu jazyka JavaScript z webového prohlížeče klienta). Služba používá <xref:System.ServiceModel.Web.WebGetAttribute> atribut zajistíte, že služba reaguje na požadavky HTTP GET a je nakonfigurován na použití formátu dat JavaScript Object Notation (JSON) pro odpovědi.  
  
 Podpora pro AJAX ve službě WCF je optimalizovaná pro použití s technologií ASP.NET AJAX prostřednictvím `ScriptManager` ovládacího prvku. Příklad použití WCF pomocí ASP.NET AJAX, najdete v článku [AJAX ukázky](https://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  Postupu a sestavení pokyny k instalaci pro tuto ukázku se nachází na konci tohoto tématu.  
  
 V následujícím kódu <xref:System.ServiceModel.Web.WebGetAttribute> atributu se použije pro `Add` operace Ujistěte se, že služba reaguje na požadavky HTTP GET. Tento kód použije GET pro zjednodušení (lze vytvořit požadavek HTTP GET z libovolného webového prohlížeče). Také vám pomůže získat povolit ukládání do mezipaměti. Chybí výchozí hodnota je HTTP POST `WebGetAttribute` atribut.  

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

 Používá ukázkový soubor SVC <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, který přidá <xref:System.ServiceModel.Description.WebScriptEndpoint> standardní koncový bod ke službě. Koncový bod je nakonfigurována na prázdnou adresu vzhledem k souboru SVC. To znamená, že je adresa služby http://localhost/ServiceModelSamples/service.svc, se žádné další přípony jiný než název operace.  

```svc
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>
```

 <xref:System.ServiceModel.Description.WebScriptEndpoint> Je předem nakonfigurovaný k zpřístupnění služby ze stránky technologie ASP.NET AJAX klienta. Následující části v souboru Web.config je možné provést další změny konfigurace koncového bodu. Je možné odebrat, pokud nejsou potřeba žádné další změny.  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webScriptEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name=""  />  
    </webScriptEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint> Nastaví výchozí formát dat pro službu do formátu JSON místo XML. Abyste mohli vyvolat službu, přejděte na http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 po dokončení sady si a sestavte kroky uvedené dále v tomto tématu. Tato funkce testování se povoluje pomocí požadavku HTTP GET.  
  
 Klient SimpleAjaxClientPage.aspx webová stránka obsahuje kód technologie ASP.NET se vyvolat službu pokaždé, když uživatel klikne jedno z tlačítek operace na stránce. `ScriptManager` Ovládací prvek se používá aby proxy pro službu pomocí JavaScriptu.  

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```

 Místní proxy server je vytvořena instance a operace jsou vyvolány pomocí následujícího kódu jazyka JavaScript.  

```javascript
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```

 Pokud je volání služby úspěšná, kód vyvolá `onSuccess` obslužnou rutinu a výsledek operace se zobrazí v textovém poli.  

```javascript
function onSuccess(mathResult){  
     document.getElementById("result").value = mathResult;  
}
```

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
  
## <a name="see-also"></a>Viz také
