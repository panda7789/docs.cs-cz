---
title: Základní služba AJAX
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 2d3770630df693093b05868f00c409f8245f858b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925241"
---
# <a name="basic-ajax-service"></a>Základní služba AJAX
Tato ukázka předvádí, jak použít Windows Communication Foundation (WCF) k vytvoření základní služby JavaScriptu (ASP.NET Asynchronous JavaScript and XML) (služba, ke které máte přístup pomocí kódu jazyka JavaScript z klienta webového prohlížeče). Služba používá <xref:System.ServiceModel.Web.WebGetAttribute> atribut k zajištění toho, že služba reaguje na požadavky HTTP GET a je nakonfigurována tak, aby pro odpovědi používala formát dat JavaScript Object Notation (JSON).  
  
 Podpora AJAX ve WCF je optimalizovaná pro použití s ASP.NET AJAX prostřednictvím `ScriptManager` ovládacího prvku. Příklad použití WCF s ASP.NET AJAX naleznete v [ukázkách AJAX](ajax.md).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 V následujícím kódu <xref:System.ServiceModel.Web.WebGetAttribute> je atribut použit `Add` pro operaci, aby bylo zajištěno, že služba reaguje na požadavky HTTP GET. Kód používá GET pro jednoduchost (požadavek HTTP GET můžete vytvořit z libovolného webového prohlížeče). Můžete také použít GET a povolit ukládání do mezipaměti. HTTP post je výchozím nastavením při nepřítomnosti `WebGetAttribute` atributu.  

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

 Ukázkový soubor. svc používá <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, který ke službě <xref:System.ServiceModel.Description.WebScriptEndpoint> přidá standardní koncový bod. Koncový bod je nakonfigurovaný na prázdné adrese relativní vzhledem k souboru. svc. To znamená, že adresa služby je `http://localhost/ServiceModelSamples/service.svc`bez dalších přípon, než je název operace.  

```svc
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>
```

 <xref:System.ServiceModel.Description.WebScriptEndpoint> Je předem nakonfigurovaný tak, aby služba byla přístupná z klientské stránky ASP.NET AJAX. Následující oddíl v souboru Web. config lze použít k provedení dalších změn konfigurace koncového bodu. Tuto možnost lze odebrat, pokud nejsou vyžadovány žádné další změny.  
  
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
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint> Nastaví výchozí formát dat pro službu na JSON namísto XML. Chcete-li vyvolat službu, přejděte `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` na adresu po dokončení kroků nastavení a sestavení, které jsou uvedeny dále v tomto tématu. Tato funkce testování je povolena pomocí požadavku HTTP GET.  
  
 Klientská webová stránka SimpleAjaxClientPage. aspx obsahuje kód ASP.NET k vyvolání služby vždy, když uživatel klikne na stránku s jedním z těchto tlačítek operace. `ScriptManager` Ovládací prvek slouží k vytvoření proxy serveru pro přístup k službě prostřednictvím JavaScriptu.  

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```

 Instance místního proxy serveru a operace jsou vyvolány pomocí následujícího kódu JavaScriptu.  

```javascript
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```

 Pokud je volání služby úspěšné, kód vyvolá `onSuccess` obslužnou rutinu a výsledek operace se zobrazí v textovém poli.  

```javascript
function onSuccess(mathResult){  
     document.getElementById("result").value = mathResult;  
}
```

> [!IMPORTANT]
>  Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
