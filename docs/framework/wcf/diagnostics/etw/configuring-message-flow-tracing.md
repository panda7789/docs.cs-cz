---
title: Konfigurace trasování toku zpráv
ms.date: 03/30/2017
ms.assetid: 15571ca2-bee2-47fb-ba10-fcbc09152ad0
ms.openlocfilehash: b01a06a50fbb5962fe87c3426957b3294b1bf3ab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917934"
---
# <a name="configuring-message-flow-tracing"></a>Konfigurace trasování toku zpráv
Pokud je povoleno trasování aktivit Windows Communication Foundation (WCF), jsou koncovým aktivitám přiřazeny logické aktivity v rámci zásobníku WCF. V [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)]systému je teď k dispozici vyšší verze výkonu této funkce, která funguje s trasováním událostí pro Windows (ETW) s názvem trasování toku zpráv. Pokud je tato možnost povolená, koncová ID aktivit se přijímají z (nebo jsou přiřazená k prázdným) příchozím zprávám a šíří se do všech trasovacích událostí, které se emitují po dekódování kanálu. Zákazníci mohou tuto funkci použít k rekonstrukci toků zpráv s protokoly trasování z různých služeb po dekódování.  
  
 Trasování lze povolit po zjištění problému s aplikací a následném vypnutí po vyřešení problému.  
  
## <a name="enabling-tracing"></a>Povolení trasování  
 Můžete povolit trasování toku zpráv nastavením prvku konfigurace .NET Framework 4 `messageFlowTracing` na `true`, jak je znázorněno v následujícím příkladu.  
  
```xml  
<system.servicemodel>  
  <diagnostics>  
    <endToEndTracing propagateActivity="true" messageFlowTracing="true" />  
  </diagnostics>  
</system.servicemodel>  
```  
  
> [!NOTE]
> Vzhledem k `endToEndTracing` tomu, že se element konfigurace nachází v souboru Web. config, nelze jej dynamicky konfigurovat stejným způsobem jako ETW. Aby se element Configuration mohl projevit, musí být aplikace recyklovaná. `endToEndTracing`  
  
 Aktivity jsou sladěné o výměnu identifikátoru s názvem ID aktivity. Tento identifikátor je identifikátor GUID a je generován třídou System. Diagnostics. CorrelationManager. Pokud pracujete s System. Diagnostics. Trace. CorrelationManager. ActivityID, zajistěte, aby byla hodnota nastavena na hodnotu původní, když se ovládací prvek spuštění přenáší zpět do kódu WCF.  Také při použití asynchronního programovacího modelu WCF zajistěte, aby byl mezi vlákny přenesen System. Diagnostics. Trace. CorrelationManager. ActivityID.  
  
## <a name="message-flow-tracing-and-rest-services"></a>Sledování toku zpráv a služby REST  
 Trasování toku zpráv vám umožňuje trasovat konec žádosti na konec.  Pomocí služeb založených na protokolu SOAP je ID aktivity odesíláno v hlavičce zprávy protokolu SOAP. Žádosti REST tuto hlavičku neobsahují, takže místo toho se použije speciální hlavička události HTTP. Následující fragment kódu ukazuje, jak lze programově načíst hodnotu ID aktivity:  
  
```csharp
Object output = null;
if (OperationContext.Current.IncomingMessageProperties.TryGetValue(HttpRequestMessageProperty.Name, out output))
{
   HttpRequestMessageProperty httpHeaders = output as HttpRequestMessageProperty;
   // Retrieve the Activity Id from the HTTP header    string e2eId = httpHeaders.Headers["E2EActivity"];
   // ...
}
```

 Hlavičku můžete programově přidat pomocí následujícího kódu:  
  
```csharp  
HttpContent content = new StreamContent(contentStream);  
Guid correlation = Guid.NewGuid();  
content.Headers.Add("E2EActivity", Convert.ToBase64String(correlation.ToByteArray()));  
```
