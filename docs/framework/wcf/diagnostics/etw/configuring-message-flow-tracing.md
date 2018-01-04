---
title: "Konfigurace trasování toku zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 15571ca2-bee2-47fb-ba10-fcbc09152ad0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8df32a64c07db8a45dfb41a46e7a65a92fbef434
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-message-flow-tracing"></a>Konfigurace trasování toku zpráv
Když [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] je povolené trasování aktivity, začátku do konce ID aktivit jsou přiřazeny logické aktivity v rámci [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zásobníku. V [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)], je teď vyšší výkon verze této funkce, která funguje s událostí trasování pro Windows (ETW) názvem trasování toku zpráv. Když je povolené, ID aktivit začátku do konce převzat ze (nebo přiřazená, pokud je prázdný) příchozí zprávy a jsou rozšířen do všech událostí trasování, vydávané po zpráva má byla dekódovat pomocí kanálu. Zákazníci mohou pomocí této funkce lze po dekódování rekonstrukci toky zprávu s protokoly trasování z jiné služby.  
  
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
