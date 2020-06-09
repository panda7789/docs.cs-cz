---
title: Přenos
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: 52b0cf35a2f8bab17252d3711f3143738c2bc39c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587765"
---
# <a name="transfer"></a>Přenos
Toto téma popisuje přenos v modelu trasování aktivity Windows Communication Foundation (WCF).  
  
## <a name="transfer-definition"></a>Definice přenosu  
 Přenosy mezi aktivitami reprezentují příčinné vztahy mezi událostmi v souvisejících aktivitách v rámci koncových bodů. Dvě aktivity souvisejí s přenosy při řízení toků mezi těmito aktivitami, například volání metody přechází přes hranice aktivity. Pokud jsou v rámci služby WCF Příchozí bajty na službu, je aktivita naslouchání v aktivitě přenesena do aktivity příjem bajtů, kde je objekt zprávy vytvořen. Seznam kompletních scénářů trasování a jejich činnost a návrh trasování najdete v tématu [kompletní scénáře sledování](end-to-end-tracing-scenarios.md).  
  
 Chcete-li vygenerovat trasování přenosu, použijte `ActivityTracing` nastavení ve zdroji trasování, jak je znázorněno v následujícím kódu konfigurace.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a>Použití přenosu ke korelaci aktivit v rámci koncových bodů  
 Aktivity a přenosy umožňují uživateli probabilistically najít hlavní příčinu chyby. Pokud například přenášíme mezi aktivitami M a N v komponentách M a N a dojde k selhání, dojde v N pravém okamžiku po převodu zpět na M, takže můžeme vykreslit závěr, že je pravděpodobný, aby se data back-N přenesla do M.  
  
 Trasování přenosu je vygenerováno z aktivity M k aktivitě N, pokud existuje tok řízení mezi M a N. Například N provede nějakou práci pro M, protože volání metody přebírá hranice aktivit. N možná již existuje nebo byl vytvořen. N je založen na M, pokud N je nová aktivita, která provádí určitou práci pro M.  
  
 Přenos z M na N se nesmí následován přenosem zpátky z N do M. Důvodem je to, že M dokáže vytvořit určitou práci v N a Nesledovat, když N dokončí tuto práci. Ve skutečnosti může M skončit, než N dokončí jeho úlohu. K tomu dojde v aktivitě "Open ServiceHost" (M), která vytvoří aktivity naslouchacího procesu (N) a pak se ukončí. Přenos zpátky z N do M znamená, že N dokončila se práce související s M.  
  
 N může pokračovat v provádění jiných zpracování, které nesouvisí s M, například stávající aktivita ověřovatele (N), která udržuje požadavky na přihlášení (M) z různých přihlašovacích aktivit.  
  
 Vztah vnořování nemusí nutně existovat mezi aktivitami M a N. K tomu může dojít z důvodu dvou důvodů. První, když aktivita M nemonitoruje skutečné zpracování provedené v N, i když M iniciované N. Sekunda, pokud N již existuje.  
  
## <a name="example-of-transfers"></a>Příklad přenosů  
 Následující seznam obsahuje dva příklady přenosu.  
  
- Při vytváření hostitele služby získá konstruktor řízení z volajícího kódu nebo volání přenese do konstruktoru. Po dokončení zpracování konstruktoru vrátí řízení volajícímu kódu nebo konstruktor převede zpět na volající kód. Toto je případ vnořené relace.  
  
- Když naslouchací proces spustí zpracování dat přenosu, vytvoří nové vlákno a zahodí se k aktivitě přijímání bajtů vhodným kontextem pro zpracování, předání řízení a dat. Když vlákno dokončilo zpracování žádosti, aktivita přijetí bajtů předá do naslouchacího procesu nic zpátky. V tomto případě máme přenos v systému, ale nemusíte ho přenést z nové aktivity vlákna. Tyto dvě aktivity souvisejí, ale nejsou vnořené.  
  
## <a name="activity-transfer-sequence"></a>Sekvence přenosu aktivity  
 Sekvence přenosu aktivit ve správném formátu zahrnuje následující kroky.  
  
1. Zahájení nové aktivity, která se skládá z výběru nové gAId.  
  
2. Vygeneruje ze stávajícího ID aktivity trasování přenosu pro tento nový gAId.  
  
3. Nastavení nového ID v TLS  
  
4. Vygenerujte počáteční trasování pro indikaci začátku nové aktivity.  
  
5. Návrat k původní aktivitě se skládá z následujících:  
  
6. Poslat trasování přenosu do původního gAIdu  
  
7. Vygeneruje trasování stop k označení konce nové aktivity.  
  
8. Nastavte TLS na starou gAId.  
  
 Následující příklad kódu ukazuje, jak to provést. Tato ukázka předpokládá, že při přesunu do nové aktivity je provedeno blokující volání, včetně trasování pro pozastavení/obnovení.  
  
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

- [Konfigurace trasování](configuring-tracing.md)
- [Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Scénáře komplexního trasování](end-to-end-tracing-scenarios.md)
- [Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md)
