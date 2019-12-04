---
title: Základní služba AJAX
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 334cc9e53d7d9746c204abe37e7c30d00baa824b
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716123"
---
# <a name="basic-ajax-service"></a>Základní služba AJAX

Tato ukázka předvádí, jak použít Windows Communication Foundation (WCF) k vytvoření základní služby JavaScriptu (ASP.NET Asynchronous JavaScript and XML) (služba, ke které máte přístup pomocí kódu jazyka JavaScript z klienta webového prohlížeče). Služba používá atribut <xref:System.ServiceModel.Web.WebGetAttribute> k zajištění toho, že služba reaguje na požadavky HTTP GET a je nakonfigurována tak, aby pro odpovědi používala formát dat JavaScript Object Notation (JSON).

Podpora AJAX ve WCF je optimalizovaná pro použití s ASP.NET AJAX prostřednictvím ovládacího prvku `ScriptManager`. Příklad použití WCF s ASP.NET AJAX naleznete v [ukázkách AJAX](ajax.md).

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

V následujícím kódu je <xref:System.ServiceModel.Web.WebGetAttribute> atribut použit na operaci `Add`, aby se zajistilo, že služba reaguje na požadavky HTTP GET. Kód používá GET pro jednoduchost (požadavek HTTP GET můžete vytvořit z libovolného webového prohlížeče). Můžete také použít GET a povolit ukládání do mezipaměti. HTTP POST je výchozí při absenci atributu `WebGetAttribute`.

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

Ukázkový soubor. svc používá <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, který do služby přidá koncový bod <xref:System.ServiceModel.Description.WebScriptEndpoint> Standard. Koncový bod je nakonfigurovaný na prázdné adrese relativní vzhledem k souboru. svc. To znamená, že adresa služby je `http://localhost/ServiceModelSamples/service.svc`, bez dalších přípon, než je název operace.

`<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>`

<xref:System.ServiceModel.Description.WebScriptEndpoint> je předem nakonfigurovaný tak, aby služba byla přístupná z klientské stránky AJAX pro ASP.NET. Následující oddíl v souboru Web. config lze použít k provedení dalších změn konfigurace koncového bodu. Tuto možnost lze odebrat, pokud nejsou vyžadovány žádné další změny.

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

<xref:System.ServiceModel.Description.WebScriptEndpoint> nastaví výchozí formát dat pro službu na JSON namísto XML. Chcete-li vyvolat službu, přejděte na `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` po dokončení kroků nastavení a sestavení, které jsou uvedeny dále v tomto tématu. Tato funkce testování je povolena pomocí požadavku HTTP GET.

Klientská webová stránka SimpleAjaxClientPage. aspx obsahuje kód ASP.NET k vyvolání služby vždy, když uživatel klikne na stránku s jedním z těchto tlačítek operace. `ScriptManager` ovládací prvek slouží k vytvoření proxy serveru pro přístup k službě prostřednictvím JavaScriptu.

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

Pokud je volání služby úspěšné, kód vyvolá obslužnou rutinu `onSuccess` a výsledek operace se zobrazí v textovém poli.

```javascript
function onSuccess(mathResult){
     document.getElementById("result").value = mathResult;
}
```

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`
