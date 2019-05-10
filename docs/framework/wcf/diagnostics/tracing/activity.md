---
title: Aktivita
ms.date: 03/30/2017
ms.assetid: 70471705-f55f-4da1-919f-4b580f172665
ms.openlocfilehash: 7f498c1f2222add197f428386076148cccc9ad06
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64656296"
---
# <a name="activity"></a>Aktivita
Toto téma popisuje trasování aktivit v modelu trasování Windows Communication Foundation (WCF). Aktivity představují zpracování jednotek, které uživatel zúžit rozsah selhání. Chyby, ke kterým dochází ve stejné aktivitě přímo souvisí. Například operace selže, protože zpráva dešifrování se nezdařilo. Zobrazí trasování pro operace a selhání dešifrování zprávy do stejné aktivity zobrazující přímá korelace mezi dešifrování chyba a Chyba žádosti.  
  
## <a name="configuring-activity-tracing"></a>Konfigurace trasování aktivity  
 WCF poskytuje předdefinované aktivity pro zpracování aplikací (viz [seznam aktivit](../../../../../docs/framework/wcf/diagnostics/tracing/activity-list.md)). Můžete také definovat aktivity prostřednictvím kódu programu do skupiny uživatelů trasování. Další informace najdete v tématu [generování trasování v uživatelském kódu](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md).  
  
 Chcete-li generovat trasování aktivity za běhu, použijte `ActivityTracing` nastavení pro `System.ServiceModel` trasování zdroj, nebo jiné WCF nebo vlastního trasování zdrojů, jak je ukázáno v následujícím kódu konfigurace.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
 Informace o tom Další informace o konfiguraci elementu a atributy se používají, najdete v článku [Konfigurace trasování](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) tématu.  
  
## <a name="viewing-activities"></a>Zobrazení aktivit  
 Můžete zobrazit činnosti a jejich nástroj [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Pokud je povolená ActivityTracing, tento nástroj přebírá trasování a seřadí je podle aktivity. Můžete také zobrazit trasování přenosů. Přenos trasování označuje, jak různé aktivity se vztahují k sobě navzájem. Uvidíte, že konkrétní aktivitu způsobila druhého spuštění. Například požadavek na zprávu spuštěn bezpečnostní ověření typu handshake získat zabezpečené konverzace Token.  
  
### <a name="correlating-activities-in-service-trace-viewer"></a>Korelaci aktivit v prohlížeče trasování služeb  
 Nástroj prohlížeče trasování služeb poskytuje dvě zobrazení aktivit:  
  
- **Seznam** zobrazení, ve kterém se používá ID aktivity přímo korelovat trasování napříč procesy. Trasování z různých procesů, například klienta a služby, ale se stejným ID aktivit jsou seskupeny do stejné aktivity. Proto chybu, ke kterým dochází ve službě, která poté způsobí chybu na straně klienta i zobrazí ve stejném zobrazení aktivity v nástroji.  
  
- **Graf** zobrazení, ve kterém jsou aktivity seskupené podle procesy. V tomto zobrazení klient a služba se stejným ID aktivity mají jejich trasování v jiné aktivity. Korelovat aktivity se stejným ID aktivity v různých procesů, nástroj ukazuje zpráva toků napříč souvisejících aktivit.  
  
 Další informace a grafické zobrazení nástroje prohlížeče trasování služeb najdete na stránce [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) a [pomocí prohlížeče trasování služeb k zobrazení korelovaných trasování a Řešení potíží s](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
## <a name="defining-the-scope-of-an-activity"></a>Definování oboru aktivity  
 Aktivita je definován v době návrhu a označuje logickou jednotku práce. Přímo souvisí s vygenerovanou trasování se stejným identifikátorem aktivity, jsou součástí téže aktivity. Protože aktivity můžete překračují hranice koncový bod (požadavek), jsou definovány dva obory pro aktivitu.  
  
- `Global` obor na aplikaci. V tomto oboru aktivity je identifikován gAId identifikátoru globálně jedinečný aktivity 128 bitů. GAid je, co se šíří přes koncové body.  
  
- `Local` rozsah jeden koncový bod. V tomto oboru aktivity je identifikován jeho gAId spolu s názvem zdroje trasování výstupu trasování aktivity a ID procesu. Tato trojici představuje id místní aktivity, vytvoří. Uvedené slouží k definování hranice (místní) aktivity.  
  
## <a name="trace-schema"></a>Schéma sledování  
 Trasování může být generována pomocí žádné schéma a na platformách společnosti Microsoft. "e2e" (pro "začátku do konce") představuje běžně používané schéma. Toto schéma obsahuje identifikátor 128 bitů (gAId), název zdroje trasování a ID procesu. Ve spravovaném kódu <xref:System.Diagnostics.XmlWriterTraceListener> vysílá trasování ve schématu E2E.  
  
 Vývojáři můžou nastavit podpory, který je vygenerován pomocí trasování tak, že nastavíte <xref:System.Diagnostics.CorrelationManager.ActivityId%2A> vlastnost s identifikátorem Guid na vlákno místní úložiště (TLS). Následující příklad ukazuje to.  
  
```csharp
// set the current Activity ID to a new GUID.  
CorrelationManager.ActivityId = Guid.NewGuid();  
```
  
 Nastavení gAId v TLS bude zřejmé, při trasování jsou emitovány pomocí zdroje trasování, jak je znázorněno v následujícím příkladu.  
  
```csharp
TraceSource traceSource = new TraceSource("myTraceSource");  
traceSource.TraceEvent(TraceEventType.Warning, eventId, "Information");  
```  
  
 Trasování, protože ho budou obsahovat gAId aktuálně v protokolu TLS, název zdroje trasování, který je předán jako parametr konstruktoru zdroj trasování a ID aktuálního procesu.  
  
## <a name="activity-lifetime"></a>Doba života aktivity  
 Nejpřísnější řečeno doklad o aktivity spustí při prvním ID aktivity se používá v emitovaný trasování a končí poslední čas, který se používá v emitovaný trasování. Poskytuje sadu předdefinovaných typů trasování <xref:System.Diagnostics>, včetně spouštění a zastavování, explicitně označit hranice životního cyklu aktivit.  
  
- Spuštění: Označuje začátek aktivity. Trasování "Start" obsahuje záznam začínající nový milník zpracování. Obsahuje nové ID aktivity pro zdroj daného trasování v daného procesu, s výjimkou případů, kdy se ID aktivity šíří napříč koncovými body, v takovém případě vidíme jednu "Start" jeden koncový bod. Spouští se nová aktivita příklady vytváření nového vlákna pro zpracování, nebo zadáním nové veřejné metody.  
  
- Stop: Označuje konec aktivity. Trasování "Stop" poskytuje záznam o ukončení existující milník zpracování. Obsahuje existující ID aktivity pro zdroj daného trasování v daného procesu, s výjimkou případů, kdy se ID aktivity šíří napříč koncovými body, v takovém případě vidíme jednu "Stop" jeden koncový bod.  Zastavuje se aktivita příklady ukončuje podproces zpracování a ukončuje se metoda jehož začátku byl označený "Start" trasování.  
  
- Pozastavit: Označuje pozastavení zpracování aktivity. Trasování "Pozastavit" obsahuje existující ID aktivity, jejíž zpracování se očekává pokračovat později. Žádné trasování jsou emitovány s tímto ID mezi událostí pozastavení a obnovení z aktuálního zdroje trasování. Příklady: aktivita pozastavení při volání do funkce vnější knihovny, nebo při čekání na prostředek, jako je port dokončení vstupně-výstupních operací.  
  
- Obnovení: Označuje opětovné zpracování aktivity. Trasování "Obnovit" obsahuje existující id aktivity, jejíž poslední trasování vygenerovanou z aktuálního zdroje trasování byl "Pozastavit" trasování. Mezi příklady patří návratu z volání funkce externí knihovny nebo signalizován obnovit zpracování podle prostředků, jako je port dokončení vstupně-výstupních operací.  
  
- Přenos: Protože některé aktivity jsou způsobeny jinými uživateli nebo jiné se týkají, aktivity může souviset s další aktivity prostřednictvím "Přenést" trasování. Převod záznamů řízené vztah sady jedné aktivity do druhé  
  
 Spuštění a zastavení trasování nejsou důležité pro korelaci. Nicméně mohou pomoci zvýšit výkon, profilace a ověřování obor aktivit.  
  
 Pomocí těchto typů, nástroje můžete optimalizovat navigace protokoly trasování a hledat okamžitě souvisejících událostí do stejné aktivity nebo události v související aktivity, pokud nástroj dodržuje přenos trasování. Například nástroje se zastaví analýzu protokolů pro danou aktivitu, když se jim spuštění/zastavení trasování.  
  
 Tyto typy trasování lze použít také pro profilování. Prostředky spotřebované mezi značkami spouštění a zastavování představují celkový čas aktivity, včetně logické obsažené aktivity. Odečtením časových intervalů mezi trasování pozastavení a obnovení poskytuje skutečné aktivity čas.  
  
 Zastavení trasování je také užitečné hlavně při ověřování oboru implementovaných aktivit. Pokud některá trasování zpracování se zobrazí po zastavení trasování místo uvnitř danou aktivitu, to může naznačuje chybu v kódu.  
  
## <a name="guidelines-for-using-activity-tracing"></a>Pokyny k použití trasování činnosti  
 Následuje seznam uvádí pomocí trasování ActivityTracing (spuštění, zastavení, pozastavení, obnovení a přenos).  
  
- Trasování je orientovaný graf cyklické, ne stromu. Ovládací prvek může vrátit k aktivitě, která vytvoří podřízený proces aktivity.  
  
- Aktivita označuje hranici zpracování, což může být srozumitelné pro správce systému nebo pro možnosti podpory.  
  
- Každá metoda služby WCF, jak na klientovi a serveru, je omezená, když na začátek novou aktivitu a potom (po dokončení práce) končí nová aktivita a vrácení k aktivitě okolí.  
  
- Dlouho spuštěný (probíhající) aktivity, například naslouchat pro připojení nebo čeká na zprávy jsou reprezentovány odpovídající značek start/stop.  
  
- Aktivity aktivované příjmu nebo zpracování zprávy jsou reprezentovány hranice trasování.  
  
- Aktivity představují aktivity, ne tedy nutně objekty. Aktivita by měl být interpretován jako "k této situaci docházelo při. . . (emisí smysluplné trasování došlo k chybě)."  
  
## <a name="see-also"></a>Viz také:

- [Konfigurace trasování](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Scénáře komplexního trasování](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
- [Generování trasování v uživatelském kódu](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md)
