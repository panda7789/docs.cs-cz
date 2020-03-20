---
title: Přenos
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: e0ebfff97cd33e7a588a1ab92399a97a0fbec039
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185709"
---
# <a name="transfer"></a>Přenos
Toto téma popisuje přenos v modelu trasování aktivity Windows Communication Foundation (WCF).  
  
## <a name="transfer-definition"></a>Definice přenosu  
 Přenosy mezi aktivitami představují příčinné vztahy mezi událostmi v souvisejících aktivitách v rámci koncových bodů. Dvě aktivity souvisejí s přenosy při řízení toků mezi těmito aktivitami, například volání metody překračování hranic aktivity. V WCF při bajtů jsou příchozí na službu, listen at aktivita je převedena na příjem bajtů aktivity, kde je vytvořen objekt zprávy. Seznam scénářů trasování od konce a jejich příslušné aktivity a návrh trasování naleznete v [tématu Scénáře trasování mezi koncovými místy](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).  
  
 Chcete-li vyzařovat trasování `ActivityTracing` přenosu, použijte nastavení na zdroji trasování, jak je znázorněno následujícím konfiguračním kódem.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a>Použití přenosu ke korelaci aktivit v rámci koncových bodů  
 Aktivity a převody umožňují uživateli probabilistically vyhledat hlavní příčinu chyby. Například pokud přenášíme tam a zpět mezi aktivitami M a N v součástech M a N a k chybě dojde v N hned po převodu zpět na M, můžeme vyvodit závěr, že je to pravděpodobně způsobeno předáváním dat N zpět do M.  
  
 Trasování přenosu je emitován z aktivity M do aktivity N, pokud je tok řízení mezi M a N. Například N provádí některé práce pro M z důvodu volání metody překročení hranice aktivity. N již může existovat nebo byla vytvořena. N je zplozena M, když N je nová aktivita, která provádí některé práce pro M.  
  
 Po převodu z M na N nesmí následovat převod zpět z N do M. Důvodem je, že M může plodit nějakou práci v N a nesledovat, když N dokončí tuto práci. Ve skutečnosti M může ukončit před N dokončí svůj úkol. K tomu dochází v aktivitě "Open ServiceHost" (M), která spouští aktivity posluchače (N) a pak se ukončí. Převod zpět z N na M znamená, že N dokončil práci související s M.  
  
 N můžete pokračovat v provádění jiné zpracování nesouvisí s M, například existující ověřovací aktivity (N), který udržuje příjem žádostí o přihlášení (M) z různých aktivit přihlášení.  
  
 Vztah vnoření nemusí nutně existovat mezi aktivitami M a N. K tomu může dojít ze dvou důvodů. Za prvé, když aktivita M nesleduje skutečné zpracování provedené v N, i když M inicioval N. Za druhé, když N již existuje.  
  
## <a name="example-of-transfers"></a>Příklad převodů  
 V následujícím seznamu jsou uvedeny dva příklady přenosu.  
  
- Při vytváření hostitele služby získá konstruktor ovládací prvek z volajícího kódu nebo volajícího kódu se přenese do konstruktoru. Po dokončení provádění konstruktoru vrátí ovládací prvek volajícího kódu nebo konstruktor přenese zpět do volajícího kódu. To je případ vnořeného vztahu.  
  
- Když naslouchací proces začne zpracovávat přenosová data, vytvoří nové vlákno a předává aktivitě Příjem bajtů vhodný kontext pro zpracování, předávání řízení a dat. Po dokončení zpracování požadavku toto vlákno, příjem bajtů aktivity předává nic zpět naslouchací proces. V tomto případě máme převod v, ale žádný převod z nové aktivity vlákna. Dvě aktivity jsou související, ale nejsou vnořené.  
  
## <a name="activity-transfer-sequence"></a>Posloupnost přenosu aktivity  
 Dobře formátovaná sekvence přenosu aktivity zahrnuje následující kroky.  
  
1. Začněte novou aktivitu, která se skládá z výběru nového gAId.  
  
2. Vyzařují trasu přenosu do nového gAId z aktuálního ID aktivity.  
  
3. Nastavení nového ID v TLS  
  
4. Vyzařují počáteční trasování označující začátek nové aktivity.  
  
5. Návrat k původní činnosti se skládá z následujících:  
  
6. Vyzařují trasu přenosu do původního gAId  
  
7. Vyzařovat stopování stop, které označuje konec nové aktivity.  
  
8. Nastavte TLS na starý gAId.  
  
 Následující příklad kódu ukazuje, jak to provést. Tato ukázka předpokládá, že blokování volání je provedeno při přenosu do nové aktivity a zahrnuje stopy pozastavit nebo obnovit.  
  
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
  
## <a name="see-also"></a>Viz také

- [Konfigurace trasování](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Scénáře komplexního trasování](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
