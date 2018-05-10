---
title: Konfigurace trasování toku zpráv
ms.date: 03/30/2017
ms.assetid: 15571ca2-bee2-47fb-ba10-fcbc09152ad0
ms.openlocfilehash: 02c43b152cb1aef1684185e56eb7f172036ac46b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="configuring-message-flow-tracing"></a>Konfigurace trasování toku zpráv
Pokud je povoleno sledování aktivity Windows Communication Foundation (WCF), ID aktivit začátku do konce přiřazené k logické aktivity v rámci zásobníku WCF. V [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)], je teď vyšší výkon verze této funkce, která funguje s událostí trasování pro Windows (ETW) názvem trasování toku zpráv. Když je povolené, ID aktivit začátku do konce převzat ze (nebo přiřazená, pokud je prázdný) příchozí zprávy a jsou rozšířen do všech událostí trasování, vydávané po zpráva má byla dekódovat pomocí kanálu. Zákazníci mohou pomocí této funkce lze po dekódování rekonstrukci toky zprávu s protokoly trasování z jiné služby.  
  
 Trasování lze povolit po zjištění problému s aplikací a pak zakázáno, jakmile je problém vyřešen.  
  
## <a name="enabling-tracing"></a>Povolení trasování  
 Můžete povolit trasování toku zpráv tak na rozhraní .NET Framework 4 `messageFlowTracing` prvku konfigurace `true`, jak je znázorněno v následujícím příkladu.  
  
```xml  
<system.servicemodel>  
  <diagnostics>  
    <endToEndTracing propagateActivity="true" messageFlowTracing="true" />  
  </diagnostics>  
</system.servicemodel>  
```  
  
> [!NOTE]
>  Protože `endToEndTracing` konfigurační prvek nachází v souboru Web.config, nedá se nakonfigurovat dynamicky stejným způsobem jako trasování událostí pro Windows. Pro `endToEndTracing` element konfigurace projevila, aplikace musí být recykluje.  
  
 Aktivity jsou korelační podle výměny identifikátor s názvem ID aktivity. Tento identifikátor je identifikátor GUID a je vygenerována třídou System.Diagnostics.CorrelationManager. Pokud pracovat s System.Diagnostics.Trace.CorrelationManager.ActivityID, ujistěte se, že je hodnota nastavena na původní při přenosech řízení provádění zpět do kódu WCF.  Navíc pokud používáte asynchronní programovací model WCF Ujistěte se, že je System.Diagnostics.Trace.CorrelationManager.ActivityID přenášet mezi vláken.  
  
## <a name="message-flow-tracing-and-rest-services"></a>Trasování toku zpráv a služby REST  
 Trasování toku zpráv umožňuje trasování požadavku konce.  Založený na protokolu SOAP služby je k ní ID aktivity odeslán v hlavičce protokolu SOAP zprávy. Požadavky REST neobsahují tuto hlavičku, je místo toho použít speciální událostí hlavičku protokolu HTTP. Následující fragment kódu ukazuje, jak můžete programově načíst hodnotu ID aktivity:  
  
```csharp
Object output = null;
if (OperationContext.Current.IncomingMessageProperties.TryGetValue(HttpRequestMessageProperty.Name, out output))
{
   HttpRequestMessageProperty httpHeaders = output as HttpRequestMessageProperty;
   // Retrieve the Activity Id from the HTTP header    string e2eId = httpHeaders.Headers["E2EActivity"];
   // ...
}
```

 Prostřednictvím kódu programu, můžete přidat hlavičku pomocí následujícího kódu:  
  
```csharp  
HttpContent content = new StreamContent(contentStream);  
Guid correlation = Guid.NewGuid();  
content.Headers.Add("E2EActivity", Convert.ToBase64String(correlation.ToByteArray()));  
```
