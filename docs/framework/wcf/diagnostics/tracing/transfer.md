---
title: Přenos
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: d6ca1f8471fb1513263354e2369891bf9ffcb583
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552917"
---
# <a name="transfer"></a>Přenos
Toto téma popisuje přenosu v modelu trasování aktivity Windows Communication Foundation (WCF).  
  
## <a name="transfer-definition"></a>Definice přenosu  
 Přenosy mezi aktivitami představují příčinnou vztahy mezi událostmi v souvisejících činností v rámci koncových bodů. Dvě aktivity jsou propojeny s přenosy, když tok řízení mezi tyto aktivity, například volání metody přes hranice aktivity. Ve službě WCF když bajty příchozí službě, aktivita naslouchat na se přenesou do aktivity přijímání bajtů kde se vytvoří objekt zprávy. Seznam scénáře trasování začátku do konce a jejich odpovídajících aktivit a trasování návrhu najdete v tématu [scénáře trasování začátku do konce](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).  
  
 Chcete-li generovat přenos trasování, použijte `ActivityTracing` nastavení pro zdroj trasování, jak je ukázáno v následujícím kódu konfigurace.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a>Pomocí přenosu v korelovat aktivity v rámci koncových bodů  
 Aktivity a přenosy povolit uživateli probabilistically najít hlavní příčinu chyby. Například pokud jsme přenos vpřed a zpět mezi aktivitami M a N v uvedeném pořadí v součástech M a N a selhání se stane v pravé N po převodu zpět na M, jsme nakreslit do svého závěru, že je pravděpodobně v důsledku n. předání dat zpět do M.  
  
 Přenos trasování je vygenerován z aktivity M pro aktivitu N pokud tok řízení mezi M a N. Například N provede nějakou práci M kvůli volání metody přes hranice aktivit. Možná již existuje nebo byl vytvořen. N je vytvořený službou M, když je N novou aktivitu prováděnou práci pro M.  
  
 Přenos z M na N nemůže být následovaná převod zpět z N až M. Je to proto M můžete vytvořit podřízený práci ve N a do not track po N dokončení práce. Ve skutečnosti M může ukončit předtím, než N dokončení svých úkolů. K tomu dojde za "Hostitel služby otevřít" aktivity (M), která vytvoří naslouchací proces aktivity (N) a poté ukončí. Převod zpět z N až M znamená, že N Dokončená práce související se M.  
  
 N můžete pokračovat v provádění jiné zpracování nesouvisí se M, například existující aktivitu authenticator (N), která udržuje přijímání žádostí o přihlášení (M) z jiné aktivity.  
  
 Vztah vnoření neexistuje nutně mezi aktivitami M a N. Může to být způsobeno dva důvody. Nejprve, když aktivita M nesleduje vlastní zpracování provádět v N Přestože iniciované M N. Sekundy, když N již existuje.  
  
## <a name="example-of-transfers"></a>Příklad přenosů  
 Následující seznamy dva přenos příklady.  
  
-   Při vytváření hostitele služby konstruktoru získá kontrolu dělat volající kód nebo volající kód převede do konstruktoru. Po dokončení provádění konstruktoru vrátí řízení volajícímu kódu nebo konstruktor přenosech zpět do volající kód. To platí vnořené relace.  
  
-   Po spuštění zpracování přenosu dat naslouchací proces vytvoří nové vlákno a předá aktivitě přijímání bajtů vhodném kontextu pro zpracování a předání řízení a data. Po dokončení zpracování žádosti bylo vlákno aktivita přijímání bajtů nic předá zpět k naslouchacímu procesu. V tomto případě máme přenosu v ale nepřenášejí žádná aktivita nové vlákno. Dvě aktivity spolu souvisejí, ale ne vnořenou.  
  
## <a name="activity-transfer-sequence"></a>Pořadí aktivit přenosu  
 Pořadí přenosu ve správném formátu aktivit zahrnuje následující kroky.  
  
1.  Začněte novou aktivitu, která se skládá z výběru nového gAId.  
  
2.  Generování trasování přenos do této nové gAId z aktuální ID aktivity  
  
3.  Nastavení nového ID v TLS  
  
4.  Generuje počáteční trasování označující začátek nové aktivity podle.  
  
5.  Vrátit se k původní aktivity se skládá z následujících akcí:  
  
6.  Generování trasování do třídy přenosu původní gAId  
  
7.  Generování trasování Stop pro označení konce nová aktivita  
  
8.  Nastavte na staré gAId TLS.  
  
 Následující příklad kódu ukazuje, jak to provést. Tento příklad předpokládá blokovacího hovoru se provádí při přenosu do novou aktivitu a zahrnuje trasování operací pozastavit/pokračovat.  
  
```csharp
// 0. Create a trace source  
TraceSource ts = new TraceSource("myTS");  

// 1. remember existing ("ambient") activity for clean up  
Guid oldGuid = Trace.CorrelationManager.ActivityId;  
// this will be our new activity  
Guid newGuid = Guid.NewGuid();   

// 2. call transfer, indicating that we are switching to the new AID  
ts.TraceTransfer(667, "Transferring.", newGuid);  

// 3. Suspend the current activity.  
ts.TraceEvent(TraceEventType.Suspend, 667, "Suspend: Activity " + i-1);  

// 4. set the new AID in TLS  
Trace.CorrelationManager.ActivityId = newGuid;  

// 5. Emit the start trace  
ts.TraceEvent(TraceEventType.Start, 667, "Boundary: Activity " + i);  

// trace something  
ts.TraceEvent(TraceEventType.Information, 667, "Hello from activity " + i);  

// Perform Work  
// some work.  
// Return  
ts.TraceEvent(TraceEventType.Information, 667, "Work complete on activity " + i);   

// 6. Emit the transfer returning to the original activity  
ts.TraceTransfer(667, "Transferring Back.", oldGuid);  

// 7. Emit the End trace  
ts.TraceEvent(TraceEventType.Stop, 667, "Boundary: Activity " + i);  

// 8. Change the tls variable to the original AID  
Trace.CorrelationManager.ActivityId = oldGuid;    

// 9. Resume the old activity  
ts.TraceEvent(TraceEventType.Resume, 667, "Resume: Activity " + i-1);  
```  
  
## <a name="see-also"></a>Viz také:
- [Konfigurace trasování](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Scénáře komplexního trasování](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
