---
title: "Přenos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 40cd80b2b4e2f949b92f4c89cde6b271a502d047
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="transfer"></a>Přenos
Toto téma popisuje přenos v [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] model trasování aktivity.  
  
## <a name="transfer-definition"></a>Definice přenosu  
 Přenosy mezi aktivitami představují příčinnou vztahy mezi událostmi v souvisejících činností v rámci koncové body. Dvě aktivity souvisejí s přenosy při řízení toků mezi tyto aktivity, například volání metody při překročení hranice aktivity. V [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], když bajtů příchozí na službu, naslouchat na aktivity se přenese do aktivity přijímat bajtů, kde se má vytvořit objekt zprávy. Seznam trasování začátku do konce scénáře a jejich odpovídající aktivitu a trasování návrhu najdete v tématu [scénáře trasování začátku do konce](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).  
  
 Chcete-li emitování přenos trasování, použijte `ActivityTracing` nastavení na zdroj trasování, jak je ukázáno v následujícím kódu konfigurace.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a>Pomocí přenosu ke korelaci aktivity v rámci koncové body  
 Aktivity a přenosy povolit uživatelům probabilistically najít hlavní příčinu chyby. Pokud jsme přenosu přepínat mezi aktivitami M a N v uvedeném pořadí v součásti M a N a havárie se stane v pravé N po přenos zpět do M, jsme zakreslit závěru, že je pravděpodobně způsobená N pro předávání dat zpět na M.  
  
 Přenos trasování nevydává aktivity M aktivity N po toku řízení mezi M a N. Například N provádí některé pracovní pro M z důvodu překročení meze aktivit hranice volání metody. N možná již existuje nebo byla vytvořena. N je vytvořený službou M po N nová aktivita, která provádí některé pracovní pro M.  
  
 Přenos z M k N nesmí následovat přenos zpět z N až M. Je to proto, že se mohou provést některé pracovní v N M a není sledovat, kdy N dokončí svou práci. Ve skutečnosti M můžete ukončit předtím, než N dokončení úkolu. K tomu dochází v aktivitě "Otevřete ServiceHost" (M), který vytvoří naslouchací proces aktivity (ne) a pak se ukončí. Přenos zpět z N až M znamená, že N dokončení práce související s M.  
  
 N můžete pokračovat v provádění další zpracování, které nejsou v relaci M, například stávající ověřovací aktivitu (ne), která udržuje přijímání žádostí o přihlášení (M) z jiné přihlašovací údaje aktivit.  
  
 Vnoření relace neexistuje nutně mezi aktivitami M a N. K tomu dochází z důvodu ze dvou důvodů. První, když aktivita M nesleduje vlastní zpracování prováděla N i když iniciované M N. Druhá, když N již existuje.  
  
## <a name="example-of-transfers"></a>Příklad přenosů  
 Následující seznamy dva přenos příklady.  
  
-   Při vytváření hostitele služby konstruktoru získá kontrolu z volající kód nebo kód volání přenáší do konstruktoru. Po dokončení provádění konstruktoru volající kód vrátí ovládací prvek nebo konstruktoru přenáší zpět do volání kódu. Toto je případ vnořené relace.  
  
-   Při spuštění zpracování přenosu dat naslouchací proces vytvoří nové vlákno a předá aktivitě přijímat bajtů odpovídající kontext pro zpracování a předání řízení a data. Po dokončení zpracování požadavku daném vláknu aktivity přijímat bajtů nic předá zpět do naslouchací proces. V takovém případě máme přenos v, ale žádný přenos mimo nová aktivita přístup z více vláken. Dvě aktivity spolu souvisejí, ale není vnořený.  
  
## <a name="activity-transfer-sequence"></a>Pořadí aktivit přenosu  
 Posloupnost aktivit ve správném formátu přenos zahrnuje následující kroky.  
  
1.  Začněte novou aktivitu, který se skládá z výběru nové gAId.  
  
2.  Emitování přenos trasování do této nové gAId z ID aktuální aktivity  
  
3.  Nastavit nové ID v protokolu TLS  
  
4.  Emitování počáteční trasování označující začátek nové aktivity podle.  
  
5.  Vraťte se do původního aktivity se skládá z následujících akcí:  
  
6.  Emitování trasování do třídy přenosu původní gAId  
  
7.  Emitování Zastavit trasování k označení konce nová aktivita  
  
8.  Nastavit starý gAId TLS.  
  
 Následující příklad kódu ukazuje, jak to udělat. Tato ukázka předpokládá blokování volání, provádí při přenosu do nová aktivita a zahrnuje pozastavení nebo obnovení činnosti trasování.  
  
```  
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
 [Konfigurace trasování](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení potíží](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [Scénáře začátku do konce trasování](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [Nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
