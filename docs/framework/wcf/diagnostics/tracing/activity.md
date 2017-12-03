---
title: Aktivita
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70471705-f55f-4da1-919f-4b580f172665
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 382197f2a8d2375903f286dc5aa54ce5dc632bce
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="activity"></a>Aktivita
Toto téma popisuje aktivity trasování v [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] trasování modelu. Aktivity jsou zpracování jednotek, které pomůže uživateli zúžit obor selhání. Chyby, ke kterým dochází ve stejné aktivitě přímo souvisí. Operace se například nezdaří, protože zpráva dešifrování se nezdařilo. Trasování pro operace a Chyba při dešifrování zprávy zobrazí ve stejné aktivitě, zobrazující přímé korelace mezi chyby dešifrování a chybu požadavku.  
  
## <a name="configuring-activity-tracing"></a>Konfigurace trasování aktivity  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]obsahuje předem definovaná aktivity pro zpracování aplikace (viz [seznam aktivit](../../../../../docs/framework/wcf/diagnostics/tracing/activity-list.md)). Můžete také definovat aktivity prostřednictvím kódu programu ke skupině uživatelů trasování. Další informace najdete v tématu [generování trasování v uživatelském kódu](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md).  
  
 Pro vydávání trasování aktivity v době běhu, použijte `ActivityTracing` nastavení `System.ServiceModel` trasování zdroje nebo jiné [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] nebo vlastního trasování zdrojů, jak je ukázáno v následujícím kódu konfigurace.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
 Bližší informace o konfiguraci elementu a atributy, které používá, najdete v článku [Konfigurace trasování](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) tématu.  
  
## <a name="viewing-activities"></a>Zobrazení aktivity  
 Můžete zobrazit činnosti a jejich nástroj v [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Pokud je povoleno ActivityTracing, tento nástroj trvá trasování a řadí je na základě aktivity. Můžete také zjistit trasování přenosů. Přenos trasování Určuje, jak různé aktivity jsou vzájemně souvisí. Můžete zobrazit konkrétní aktivitu kvůli jiné spustit. Žádost o zprávu například spuštěn bezpečnostní ověření typu handshake k získání zabezpečené konverzace tokenu.  
  
### <a name="correlating-activities-in-service-trace-viewer"></a>Korelace aktivity v prohlížeče trasování služeb  
 Tento nástroj prohlížeče trasování služeb nabízí dvě zobrazení aktivit:  
  
-   **Seznam** zobrazení, kde se ID aktivity slouží ke korelaci přímo trasování napříč procesy. Trasování z různých procesů, například klienta a služby, ale se stejným ID aktivit jsou seskupeny do stejné aktivity. Proto chybu, ke kterým dochází na službu, která pak výsledkem bude chyba na straně klienta se obě zobrazí v zobrazení aktivity v nástroji.  
  
-   **Graf** zobrazení, kde jsou aktivity seskupené podle procesy. V tomto zobrazení klienta a služby se stejným ID aktivity mají jejich trasování v různé aktivity. Nástroj ke korelaci aktivity se stejným ID aktivity v různých procesů, zobrazuje zpráva toky napříč souvisejících činností.  
  
 Další informace a zobrazíte grafické zobrazení nástroje prohlížeče trasování služeb najdete v části [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) a [pomocí prohlížeče trasování služeb pro zobrazení korelační trasování a Řešení potíží s](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
## <a name="defining-the-scope-of-an-activity"></a>Definování oboru aktivity  
 Aktivita je definován v době návrhu a označuje logické jednotky práce. Přímo souvisí s emitovaného trasování se stejným identifikátorem aktivity, jsou součástí stejné aktivity. Protože aktivitu můžete napříč hranicemi koncový bod (požadavek), jsou definovány dva obory pro aktivitu.  
  
-   `Global`obor na aplikaci. V tomto rozsahu aktivita je identifikována jeho 128-bit aktivity globálně jedinečný identifikátor, gAId. GAid je co rozšířena napříč koncovými body.  
  
-   `Local`obor na jeden koncový bod. V tomto rozsahu aktivita je identifikována jeho gAId, společně s název zdroje trasování generování trasování aktivity a ID procesu Tato trojdílná se považuje za id místní aktivity, umístěné. , Které jsou uvedené se používá k definování hranice (místní) aktivity.  
  
## <a name="trace-schema"></a>Schéma trasování  
 Trasování může vygenerované pomocí žádné schéma a různé platformy Microsoft. "e2e" (pro "koncové") je běžně používané schéma. Toto schéma obsahuje identifikátor 128bitové (gAId), název zdroje trasování a ID procesu. Ve spravovaném kódu <xref:System.Diagnostics.XmlWriterTraceListener> vysílá trasování ve schématu E2E.  
  
 Mohou vývojáři nastavit podpory, které jsou vydávány s trasování nastavením <xref:System.Diagnostics.CorrelationManager.ActivityId%2A> vlastnost s identifikátorem Guid na vláken místní úložiště (TLS). Následující příklad ukazuje to.  
  
```  
// set the current Activity ID to a new GUID.  
CorrelationManager.ActivityId = Guid.NewGuid();  
```  
  
 Nastavení gAId v TLS bude zřejmá při trasování jsou vygenerované pomocí zdroj trasování, jak ukazuje následující příklad.  
  
```  
TraceSource traceSource = new TraceSource("myTraceSource");  
traceSource.TraceEvent(TraceEventType.Warning, eventId, "Information");  
```  
  
 Trasování vygenerované bude obsahovat gAId právě TLS, název zdroje trasování jako parametr předaný konstruktoru zdroj trasování a ID aktuálním procesu.  
  
## <a name="activity-lifetime"></a>Doba platnosti aktivity  
 V nejpřísnějším podmínky důkaz aktivity spustí při prvním ID aktivity se používá v emitovaného trasování a končí, kdy se používá v emitovaného trasování naposledy. Sadu předdefinovaných typů trasování jsou poskytovány <xref:System.Diagnostics>, včetně zahájení a ukončení, explicitně označit hranice životního cyklu aktivity.  
  
-   Začátek: Označuje začátek aktivity. "Start" trasování obsahuje záznam od nový milník zpracování. Obsahuje nové ID aktivity pro zdroj daného trasování v dané procesu, s výjimkou případů, kdy je ID aktivity rozšíří napříč koncovými body, v takovém případě vidíte jeden "Start" na jeden koncový bod. Spuštění nové aktivity příklady vytváření nové vlákno pro zpracování, nebo zadat novou veřejnou metodu.  
  
-   Stop: Označuje konec aktivity. Trasování "Stop" poskytuje záznam ukončení existující milník zpracování. Obsahuje existující ID aktivity pro zdroj daného trasování v dané procesu, s výjimkou případů, kdy je ID aktivity rozšíří napříč koncovými body, v takovém případě vidíme na jeden koncový bod jeden "Stop".  Zastavení aktivity příklady ukončuje podproces zpracování nebo ukončení metoda, jejíž začátku byla označený jako s "Start" trasování.  
  
-   Pozastavit: Označuje pozastavení zpracování aktivity. "Pozastavit" trasování obsahuje existující ID aktivity jejichž zpracování se očekává pokračovat později. Žádné trasování jsou vydávány s tímto ID mezi události pozastavení a obnovení v aktuálním zdroji trasování. Příklady pozastavení aktivitu při volání do funkce vnější knihovny nebo při čekání na prostředek, například k portu dokončení vstupně-výstupní operace.  
  
-   Obnovení: Označuje obnovení zpracování aktivity. "Obnovit" trasování obsahuje existující id aktivity jejichž poslední emitovaného trasování v aktuálním zdroji trasování byl "Pozastavit" trasování. Mezi příklady patří vrácení z volání funkce vnější knihovny, nebo když signál k obnovení prostředek například k portu dokončení vstupně-výstupní operace.  
  
-   Přenos: Vzhledem k tomu, že některé aktivity jsou způsobeny ostatní, nebo se týkají jiným uživatelům, aktivity může souviset s dalšími aktivitami prostřednictvím "Přenos" trasování. Přenos zaznamenává směrovanou vztah jedné aktivity do jiného  
  
 Spuštění a zastavení trasování nejsou důležité pro korelačního. Však může pomoci zvýšit výkon, profilace a oboru ověření aktivity.  
  
 Pomocí těchto typů, nástroje můžete optimalizovat navigace protokoly trasování a vyhledejte okamžitě související události téže aktivity, nebo události v související aktivity, pokud nástroj dodržuje přenos trasování. Například nástroje zastaví, analýzy protokolů pro danou aktivitu, když se jim trasování spuštění a zastavení.  
  
 Tyto typy trasování můžete použít také pro profilaci. Využívání prostředků mezi značky zahájení a ukončení představují aktivity včetně dobu, včetně obsažené logické aktivity. Odečtením časových intervalů mezi pozastavení a obnovení trasování poskytuje čas skutečné aktivity.  
  
 Zastavit trasování je také užitečné pro ověření oboru implementovaných aktivit. Pokud některé zpracování trasování se zobrazí po zastavení trasování místo uvnitř danou aktivitu, to může navrhuje vadou kódu.  
  
## <a name="guidelines-for-using-activity-tracing"></a>Pokyny k používání trasování aktivit  
 Následuje seznam uvádí pomocí trasování ActivityTracing (spuštění, zastavení, pozastavení, opětovné spuštění a přenos).  
  
-   Trasování je řízené cyklická grafu není stromu. Ovládací prvek může vrátit k aktivitě, která vytvořený aktivitu.  
  
-   Aktivita označuje zpracování hranic, která může mít smysl pro správce systému nebo o podpoře.  
  
-   Každý [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] metoda, jak na klientovi a serveru, je vázaný podle od nová aktivita a pak (po práci) ukončení nová aktivita a vrátilo se do vedlejším aktivity.  
  
-   Dlouho spuštěný (probíhající) aktivity, například naslouchat pro připojení nebo čekání zprávy jsou reprezentované pomocí odpovídající značky spuštění a zastavení.  
  
-   Aktivity aktivovány příjmu nebo zpracování zprávy, které jsou reprezentované pomocí trasování hranice.  
  
-   Aktivity představují aktivity, nikoli nutně objekty. Aktivita by měl být interpretován jako "to se děje při. . . (emisí smysluplný trasování došlo k chybě)."  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace trasování](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení potíží](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [Scénáře začátku do konce trasování](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [Nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [Generování trasování v uživatelském kódu](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md)
