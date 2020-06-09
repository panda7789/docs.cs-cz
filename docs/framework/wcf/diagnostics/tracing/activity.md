---
title: Aktivita
ms.date: 03/30/2017
ms.assetid: 70471705-f55f-4da1-919f-4b580f172665
ms.openlocfilehash: 41de6b9458feb4e1898eeac6635b74c4617885d6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602138"
---
# <a name="activity"></a>Aktivita
Toto téma popisuje trasování aktivit v modelu trasování Windows Communication Foundation (WCF). Aktivity zpracovávají jednotky, které uživatelům pomůžou zúžit rozsah selhání. Chyby, ke kterým dochází ve stejné aktivitě, se přímo vztahují. Operace může být například neúspěšná, protože dešifrování zprávy se nezdařilo. Trasování pro operaci a dešifrování zprávy se zobrazí ve stejné aktivitě, která zobrazuje přímou korelaci mezi chybou dešifrování a chybou požadavku.  
  
## <a name="configuring-activity-tracing"></a>Konfigurace trasování aktivit  
 WCF poskytuje předem definované aktivity pro zpracování aplikací (viz [seznam aktivit](activity-list.md)). Aktivity můžete také definovat programově k seskupení trasování uživatele. Další informace najdete v tématu [generování trasování uživatelského kódu](emitting-user-code-traces.md).  
  
 Chcete-li generovat trasování aktivity za běhu, použijte `ActivityTracing` nastavení pro `System.ServiceModel` zdroj trasování nebo jiné zdroje dat služby WCF nebo vlastní zdroje trasování, jak je znázorněno v následujícím kódu konfigurace.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
 Chcete-li získat další informace o konfiguračním elementu a použitých atributech, přečtěte si téma [Konfigurace trasování](configuring-tracing.md) .  
  
## <a name="viewing-activities"></a>Zobrazení aktivit  
 Aktivity a jejich nástroj můžete zobrazit v [nástroji Prohlížeč trasování služby (SvcTraceViewer. exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md). Když je povolený ActivityTracing, tento nástroj provede trasování a seřadí je na základě aktivity. Můžete také zobrazit přenosy trasování. Přenos trasování indikuje, jak vzájemně souvisí různé aktivity. Můžete vidět, že konkrétní aktivita způsobila další spuštění. Například žádost o zprávu spustila bezpečnostní signalizaci zabezpečení, aby získala zabezpečený token konverzace.  
  
### <a name="correlating-activities-in-service-trace-viewer"></a>Korelace aktivit v prohlížeči trasování služby  
 Nástroj Prohlížeč trasování služby poskytuje dvě zobrazení aktivit:  
  
- Zobrazení **seznamu** , kde se ID aktivity používá k přímému sladění trasování napříč procesy. Trasování z různých procesů, například klienta a služby, ale se stejným ID aktivity se seskupí do stejné aktivity. Proto dojde k chybě na službě, která pak způsobí chybu v klientovi, jak se v nástroji objeví v zobrazení stejné aktivity.  
  
- Zobrazení **grafu** , kde jsou aktivity seskupeny podle procesů. V tomto zobrazení klient a služba se stejným ID aktivity mají své trasování v různých aktivitách. Aby bylo možné korelovat aktivity se stejným ID aktivity v různých procesech, nástroj zobrazuje toky zpráv napříč souvisejícími aktivitami.  
  
 Další informace a pro zobrazení grafického zobrazení nástroje pro prohlížeč trasování služby naleznete v tématu Nástroj pro [Prohlížeč trasování služby (SvcTraceViewer. exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md) a [použití prohlížeče trasování služby pro zobrazení korelačních trasování a řešení potíží](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
## <a name="defining-the-scope-of-an-activity"></a>Definování rozsahu aktivity  
 Aktivita je definována v době návrhu a označuje logickou pracovní jednotku. Emitovaná trasování se stejným identifikátorem aktivity přímo souvisejí, jsou součástí stejné aktivity. Vzhledem k tomu, že aktivita může protínat hranice koncových bodů (požadavek), jsou definovány dva obory pro aktivitu.  
  
- `Global`Rozsah, na aplikaci. V tomto oboru je aktivita identifikována pomocí identifikátoru globální jedinečné aktivity (128), gAId. GAid je to, co se šíří napříč koncovými body.  
  
- `Local`Rozsah, na koncový bod. V tomto oboru je aktivita identifikována pomocí gAId spolu s názvem zdroje trasování, který emituje trasování aktivity a ID procesu. Tento s trojicí představuje ID místní aktivity, která je stanovena. Tato možnost slouží k definování (místních) hranic aktivity.  
  
## <a name="trace-schema"></a>Schéma trasování  
 Trasování je možné vysílat pomocí libovolného schématu a na platformách Microsoftu. "e2e" (pro "end to end") je běžně používané schéma. Toto schéma zahrnuje bit identifikátoru 128 (gAId), název zdroje trasování a ID procesu. Ve spravovaném kódu <xref:System.Diagnostics.XmlWriterTraceListener> emituje trasování ve schématu E2E.  
  
 Vývojáři mohou nastavit podporu, která je vygenerována pomocí trasování, nastavením <xref:System.Diagnostics.CorrelationManager.ActivityId%2A> vlastnosti s identifikátorem GUID v místním úložišti vláken (TLS). Následující příklad ukazuje to.  
  
```csharp
// set the current Activity ID to a new GUID.  
CorrelationManager.ActivityId = Guid.NewGuid();  
```
  
 Nastavení gAId v TLS bude zřejmé při vygenerování trasování pomocí zdroje trasování, jak je znázorněno v následujícím příkladu.  
  
```csharp
TraceSource traceSource = new TraceSource("myTraceSource");  
traceSource.TraceEvent(TraceEventType.Warning, eventId, "Information");  
```  
  
 Vysílané trasování bude obsahovat gAId, který je aktuálně v TLS, název zdroje trasování předaný jako parametr konstruktoru zdroje trasování a ID aktuálního procesu.  
  
## <a name="activity-lifetime"></a>Životnost aktivity  
 V nejpřísnějších termínech legitimace aktivity začíná při prvním použití ID aktivity ve vygenerovaném trasování a končí čas posledního použití ve vygenerovaném trasování. Předdefinovaná sada typů trasování je poskytována pomocí <xref:System.Diagnostics> , včetně příkazu Spustit a zastavit, aby explicitně označila hranice životnosti aktivity.  
  
- Start: označuje začátek aktivity. Trasování "Start" poskytuje záznam začátku nového milníku zpracování. Obsahuje nové ID aktivity pro daný zdroj trasování v daném procesu, s výjimkou případů, kdy je ID aktivity šířeno napříč koncovými body. v takovém případě se u každého koncového bodu zobrazí jedna položka "Start". Příklady spuštění nové aktivity zahrnují vytvoření nového vlákna pro zpracování nebo zadání nové veřejné metody.  
  
- Stop: označuje konec aktivity. Trasování "Stop" poskytuje záznam o ukončení existujícího milníku zpracování. Obsahuje existující ID aktivity pro daný zdroj trasování v daném procesu, s výjimkou případů, kdy je ID aktivity šířeno napříč koncovými body. v takovém případě se u každého koncového bodu zobrazí jedna "stopa".  Příklady zastavení aktivity zahrnují ukončení zpracovatelského vlákna nebo ukončení metody, jejíž začátek byl označený trasováním "spustit".  
  
- Suspend: označuje pozastavení zpracování aktivity. Trasování "Suspend" obsahuje existující ID aktivity, jehož zpracování se očekává později obnovit. Mezi událostmi pozastavení a obnovení z aktuálního zdroje trasování nejsou vygenerována žádná trasování s tímto ID. Mezi příklady patří pozastavení aktivity při volání do externí knihovny nebo při čekání na prostředek, jako je vstupně-výstupní port dokončení.  
  
- Resume: označuje pokračování zpracování aktivity. Trasování "obnovení" obsahuje existující ID aktivity, jehož poslední vysílané trasování z aktuálního zdroje trasování bylo "pozastavit" trasování. Příklady zahrnují návrat z volání externí knihovny nebo při signalizaci pro pokračování v zpracování pomocí prostředku, jako je například port pro dokončení I/O.  
  
- Přenos: vzhledem k tomu, že některé aktivity jsou způsobené ostatními nebo se vztahují k ostatním, aktivity mohou souviset s ostatními aktivitami prostřednictvím trasování "přenos". Přenos zaznamenává přímý vztah jedné aktivity k druhému.  
  
 Trasování spouštění a zastavování nejsou pro korelaci kritická. Můžou vám ale pomáhat při zvyšování výkonu, profilování a ověřování rozsahu aktivity.  
  
 Pomocí těchto typů mohou nástroje optimalizovat navigaci v protokolech trasování a vyhledat okamžitě související události stejné aktivity nebo události v souvisejících aktivitách, pokud nástroj následuje přenos trasování. Nástroje například přestanou analyzovat protokoly pro danou aktivitu, když uvidí trasování spustit/zastavit.  
  
 Tyto typy trasování lze také použít k profilaci. Prostředky spotřebované mezi značkami začátek a zastavení reprezentují celkovou dobu aktivity včetně obsažených logických aktivit. Odčítání časových intervalů mezi trasováním pozastavení a obnovení poskytuje skutečný čas aktivity.  
  
 Trasování stop je také užitečné zejména při ověřování rozsahu implementovaných aktivit. Pokud se některé trasování zpracování zobrazí po stopovém trasování namísto v rámci dané aktivity, může to mít za to chybu kódu.  
  
## <a name="guidelines-for-using-activity-tracing"></a>Pokyny k používání trasování aktivit  
 Následuje návod pro použití trasování ActivityTracing (spuštění, zastavení, pozastavení, obnovení a přenos).  
  
- Trasování je řízený cyklický graf, nikoli strom. Můžete vrátit řízení k aktivitě, která vytvořila aktivitu.  
  
- Aktivita označuje hranici zpracování, která může být smysluplná pro správce systému nebo pro podporu.  
  
- Každá metoda WCF na klientovi i na serveru je svázána zahájením nové aktivity, poté (po dokončení práce) ukončením nové aktivity a návratem do okolní aktivity.  
  
- Dlouhotrvající (pokračující) aktivity, jako je naslouchání pro připojení nebo čekání na zprávy, jsou reprezentovány odpovídajícími značkami spuštění/zastavení.  
  
- Aktivity aktivované příjmem nebo zpracováním zprávy jsou reprezentovány hranicemi trasování.  
  
- Aktivity reprezentují aktivity, ne nutně objekty. Aktivita by měla být interpretována jako "k tomu došlo, když se děje. . . (došlo k smysluplné vyměření trasování). "  
  
## <a name="see-also"></a>Viz také

- [Konfigurace trasování](configuring-tracing.md)
- [Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Scénáře komplexního trasování](end-to-end-tracing-scenarios.md)
- [Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md)
- [Generování trasování v uživatelském kódu](emitting-user-code-traces.md)
