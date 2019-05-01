---
title: Konfigurace trasování toku zpráv
ms.date: 03/30/2017
ms.assetid: 15571ca2-bee2-47fb-ba10-fcbc09152ad0
ms.openlocfilehash: 02c43b152cb1aef1684185e56eb7f172036ac46b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61999515"
---
# <a name="configuring-message-flow-tracing"></a>Konfigurace trasování toku zpráv
Pokud je povoleno trasování činnosti Windows Communication Foundation (WCF), ID aktivit začátku do konce se přiřadí k logické aktivity v rámci zásobníku WCF. V [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)], je teď vyšší výkon verze této funkce, která funguje s Event Tracing for Windows (ETW) volá trasování toku zpráv. Při povolení začátku do konce ID aktivit na základě (nebo přiřazená, pokud je prázdný) příchozí zprávy a jsou rozšíří do všech událostí trasování, které jsou emitovány po zpráva má se dekódovat na kanálu. Zákazníci mohou tuto funkci používat k rekonstrukci po dekódování zprávy toků s protokoly trasování z různých služeb.  
  
 Trasování lze povolit po zjištění problému s aplikací a pak zakázané po vyřešení problému.  
  
## <a name="enabling-tracing"></a>Povolení trasování  
 Můžete povolit trasování toku zpráv tak, že nastavíte rozhraní .NET Framework 4 `messageFlowTracing` prvku konfigurace `true`, jak je znázorněno v následujícím příkladu.  
  
```xml  
<system.servicemodel>  
  <diagnostics>  
    <endToEndTracing propagateActivity="true" messageFlowTracing="true" />  
  </diagnostics>  
</system.servicemodel>  
```  
  
> [!NOTE]
>  Vzhledem k tomu, `endToEndTracing` element konfigurace se nachází v souboru Web.config, nedá se nakonfigurovat dynamicky stejným způsobem jako trasování událostí pro Windows. Pro `endToEndTracing` element konfigurace projevila, aplikace musí být recyklován.  
  
 Aktivity se korelují podle výměna identifikátor označovaný jako ID aktivity. Tento identifikátor je identifikátor GUID a vygeneruje třídu System.Diagnostics.CorrelationManager. Pokud budete manipulovat s System.Diagnostics.Trace.CorrelationManager.ActivityID, ujistěte se, že hodnota je nastavena na původní při předání řízení provádění zpět na kód WCF.  Navíc pokud použijete asynchronního programovacího modelu WCF Ujistěte se, že System.Diagnostics.Trace.CorrelationManager.ActivityID převodu mezi vlákna.  
  
## <a name="message-flow-tracing-and-rest-services"></a>Trasování toku zpráv a služby REST  
 Trasování toku zpráv umožňuje sledovat žádost o komplexní.  ID aktivity služby založené na protokolu SOAP je odesláno jako záhlaví zprávy protokolu SOAP. Požadavky REST neobsahují této hlavičky, takže místo ní se použije zvláštní záhlaví HTTP události. Následující fragment kódu ukazuje, jak můžete programově načítat hodnotu ID aktivity:  
  
```csharp
Object output = null;
if (OperationContext.Current.IncomingMessageProperties.TryGetValue(HttpRequestMessageProperty.Name, out output))
{
   HttpRequestMessageProperty httpHeaders = output as HttpRequestMessageProperty;
   // Retrieve the Activity Id from the HTTP header    string e2eId = httpHeaders.Headers["E2EActivity"];
   // ...
}
```

 Můžete programově přidat záhlaví pomocí následujícího kódu:  
  
```csharp  
HttpContent content = new StreamContent(contentStream);  
Guid correlation = Guid.NewGuid();  
content.Headers.Add("E2EActivity", Convert.ToBase64String(correlation.ToByteArray()));  
```
